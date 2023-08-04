# Okul-Projesi-Database-Tasarimi
#Egitim Projemdeki SQL Odevim 



Tüm tablolarda bulunan 	[Id] [int] IDENTITY(1,1) NOT NULL;
1) [Id] : Bu alan benzersiz bir kimlik atamak için kullanılan bir tamsayı (integer) alanıdır. 
2) IDENTITY(1,1): Bu alan otomatik artan (auto-increment) özelliği sağlar ve her yeni bilgi eklendiğinde Id'nin otomatik olarak bir birim artacağı anlamına gelir. 
3) NOT NULL: bu alan her zaman bir değeri olması gerektiğini belirtir, yani boş (NULL) değerlere izin vermez.


Users tablosu, okulla ilişkili her türden kişi için genel bilgileri içerir. (öğrenciler, öğretmenler, idareciler vb.)
1) [Id]           : Her kullanıcıya benzersiz bir kimlik (UserID) atanır. 
2) [Name]         : Bu alanda ilgili kullanıcının ad ve soyad bilgileri tutulur.
3) [Email]        : Bu alanda kullanıcının e-posta adresi tutulur.
4) [PhoneNumber]  : Bu alanda kullanıcının telefon numarası tutulur.

``` SQL
CREATE TABLE [dbo].[Users](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [varchar](50) NOT NULL,
	[Email] [varchar](50) NOT NULL,
	[PhoneNumber] [varchar](20) NOT NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```

Students tablosu, öğrencilere ait detayları içerir.
1) [UserId]             : Users tablosu ile UserId alanı üzerinden ilişkilendirilir.
2) [ParentsContactInfo] : Öğrencinin velisinin iletişim bilgileri tutulur.
3) [ClassId]            : Kayıtlı olduğu sınıfın ID'si burada tutulur.
4) [DepartmentId]       : Öğrencinin kayıtlı olduğu bölümün kimliği tutulur. 

```SQL 
CREATE TABLE [dbo].[Students](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[UserId] [int] NOT NULL,
	[ParentsContactInfo] [varchar](100) NOT NULL,
	[ClassId] [int] NOT NULL,
	[DepartmentId] [int] NOT NULL,
 CONSTRAINT [PK_Students] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
