# SQL-SchoolProject

```
USE [master]
GO
/****** Object:  Database [SchoolProject]    Script Date: 1.08.2023 04:10:15 ******/
CREATE DATABASE [SchoolProject]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'SchoolProject', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS02\MSSQL\DATA\SchoolProject.mdf' , SIZE = 73728KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'SchoolProject_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS02\MSSQL\DATA\SchoolProject_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT, LEDGER = OFF
GO
ALTER DATABASE [SchoolProject] SET COMPATIBILITY_LEVEL = 160
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [SchoolProject].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [SchoolProject] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [SchoolProject] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [SchoolProject] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [SchoolProject] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [SchoolProject] SET ARITHABORT OFF 
GO
ALTER DATABASE [SchoolProject] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [SchoolProject] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [SchoolProject] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [SchoolProject] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [SchoolProject] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [SchoolProject] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [SchoolProject] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [SchoolProject] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [SchoolProject] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [SchoolProject] SET  DISABLE_BROKER 
GO
ALTER DATABASE [SchoolProject] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [SchoolProject] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [SchoolProject] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [SchoolProject] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [SchoolProject] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [SchoolProject] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [SchoolProject] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [SchoolProject] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [SchoolProject] SET  MULTI_USER 
GO
ALTER DATABASE [SchoolProject] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [SchoolProject] SET DB_CHAINING OFF 
GO
ALTER DATABASE [SchoolProject] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [SchoolProject] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [SchoolProject] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [SchoolProject] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
ALTER DATABASE [SchoolProject] SET QUERY_STORE = ON
GO
ALTER DATABASE [SchoolProject] SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 30), DATA_FLUSH_INTERVAL_SECONDS = 900, INTERVAL_LENGTH_MINUTES = 60, MAX_STORAGE_SIZE_MB = 1000, QUERY_CAPTURE_MODE = AUTO, SIZE_BASED_CLEANUP_MODE = AUTO, MAX_PLANS_PER_QUERY = 200, WAIT_STATS_CAPTURE_MODE = ON)
GO
USE [SchoolProject]
GO
/****** Object:  Table [dbo].[Students]    Script Date: 1.08.2023 04:10:15 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
```
  
Bu SQL betiği, Microsoft SQL Server veritabanı yönetim sistemi için bir veritabanı oluşturma ve yapılandırma işlemleri içermektedir. İşlemleri aşağıda açıklıyorum:

CREATE DATABASE [SchoolProject]: Bu komut, "SchoolProject" adında yeni bir veritabanı oluşturur. Veritabanı, "master" veritabanına bağlıdır.

CONTAINMENT = NONE: Veritabanı yalıtımsız modda oluşturulur.

ON PRIMARY: Veritabanının veri dosyalarının nerede saklanacağını belirtir. Bu durumda, "PRIMARY" adında bir dosya grubu kullanılmıştır.

FILENAME: Veritabanı dosyalarının fiziksel yolunu belirtir.

SIZE: Veritabanının ilk boyutunu belirtir (KB cinsinden).

MAXSIZE: Veritabanının maksimum boyutunu belirtir (UNLIMITED olarak ayarlanmış).

FILEGROWTH: Dosyanın otomatik büyüme miktarını belirtir (KB cinsinden).

Ve ardından, veritabanı üzerinde çeşitli ayarlamalar yapmak için ALTER DATABASE komutları gelir. Bu komutlar, örneğin ANSI ayarları, otomatik istatistik güncellemesi, kullanıcı oturum açma ayarları, çeşitli optimizasyonlar ve sorgu depolama gibi veritabanının davranışını ve performansını etkileyen ayarları yapılandırmak için kullanılır.

Son olarak, veritabanı içinde "Students" adında bir tablo oluşturulması için ilgili SQL kodu bulunmaktadır. 

```
CREATE TABLE [dbo].[Students](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[LevelId] [int] NOT NULL,
	[ClassId] [int] NOT NULL,
	[Name] [nvarchar](50) NOT NULL,
	[Surname] [nvarchar](50) NOT NULL,
	[Email] [nvarchar](100) NOT NULL,
	[PhoneNumber] [nvarchar](11) NULL,
	[MotherName] [nvarchar](50) NOT NULL,
	[FatherName] [nvarchar](50) NOT NULL,
	[ParentPhoneNumber] [nvarchar](11) NOT NULL,
	[IsActive] [bit] NULL,
	[CreatedProfessionId] [int] NULL,
	[CreatedDate] [datetime] NULL,
	[UpdatedProfessionId] [int] NULL,
	[UpdatedDate] [datetime] NULL,
```

**AÇIKLAMA:**  

Students Tablosu, aşağıdaki sütunları içermektedir:  
*Id:* Öğrenci kimlik numarasını temsil eden benzersiz bir tamsayı değeri.  
*LevelId:* Öğrencinin seviyesini belirten tamsayı değeri.  
*ClassId:* Öğrencinin sınıfını belirten tamsayı değeri.  
*Name:* Öğrencinin adını temsil eden metinsel değer (50 karakter veya daha az).  
*Surname:* Öğrencinin soyadını temsil eden metinsel değer (50 karakter veya daha az).  
*Email:* Öğrencinin e-posta adresini temsil eden metinsel değer (100 karakter veya daha az).  
*PhoneNumber:* Öğrencinin telefon numarasını temsil eden metinsel değer (11 karakter uzunluğunda, opsiyonel).  
*MotherName:* Öğrencinin annesinin adını temsil eden metinsel değer (50 karakter veya daha az).  
*FatherName:* Öğrencinin babasının adını temsil eden metinsel değer (50 karakter veya daha az).  
*ParentPhoneNumber:* Öğrencinin velisinin telefon numarasını temsil eden metinsel değer (11 karakter uzunluğunda).  
*IsActive:* Öğrencinin etkinlik durumunu temsil eden mantıksal değer (aktif ise 1, değilse 0 veya boş).  
*CreatedProfessionId:* Kayıt oluşturulduğunda atanmış olan meslek kimlik numarasını temsil eden tamsayı değeri (opsiyonel).  
*CreatedDate:* Kaydın oluşturulduğu tarihi ve saatini temsil eden değer (opsiyonel).  
*UpdatedProfessionId:* Son güncelleme yapıldığında atanmış olan meslek kimlik numarasını temsil eden tamsayı değeri (opsiyonel).  
*UpdatedDate:* Son güncelleme tarihini ve saatini temsil eden değer (opsiyonel).  

**Notlar**  

Bu tablo, öğrencilerin temel bilgilerini içeren verileri saklamak için tasarlanmıştır.  
IsActive sütunu, öğrencinin etkin veya pasif olduğunu belirtmek için kullanılabilir.  
CreatedProfessionId ve UpdatedProfessionId sütunları, verilerin oluşturulduğu ve güncellendiği meslek kimlik numaralarını ilişkilendirmek için kullanılabilir.  
CreatedDate ve UpdatedDate sütunları, verilerin oluşturulma ve güncellenme zamanlarını saklamak için kullanılabilir.  
PhoneNumber sütunu opsiyoneldir, çünkü bazı öğrencilerin telefon numaraları olmayabilir.  
Bu tabloyu kullanarak, öğrencilere ilişkin verileri kolayca saklayabilir ve yönetebilirsiniz.  


```
 CONSTRAINT [PK_Students] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  View [dbo].[vwActiveStudentsView]    Script Date: 1.08.2023 04:10:16 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE VIEW [dbo].[vwActiveStudentsView] AS
SELECT Id, Name, Surname, Email, PhoneNumber
FROM Students
WHERE IsActive = 1;
GO
/****** Object:  Table [dbo].[Exams]    Script Date: 1.08.2023 04:10:16 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
```

AÇIKLAMA:  

Bu SQL kod bloğu, veritabanında "Students" tablosu için birincil anahtar kısıtlaması oluşturan, "vwActiveStudentsView" isimli bir görünüm tanımlayan ve başlangıç aşamasında olan "Exams" tablosu için bir tablo oluşturmaya çalışan işlemleri içermektedir.  
İşlemleri kısaca açıklayalım:

CONSTRAINT [PK_Students] PRIMARY KEY CLUSTERED: Bu bölüm, "Students" tablosunda "Id" sütununu temel alarak birincil anahtar kısıtlaması oluşturur. "PK_Students" adında bir kısıtlama olarak adlandırılmıştır ve "Id" sütunu kümeleşmiş bir şekilde birincil anahtar olarak tanımlanmıştır. Bu, "Id" sütununun her bir satırda benzersiz ve sıralı değerlere sahip olduğu anlamına gelir.

CREATE VIEW [dbo].[vwActiveStudentsView] AS: Bu bölüm, "vwActiveStudentsView" adlı bir görünüm oluşturur. Görünüm, "Students" tablosundaki "Id", "Name", "Surname", "Email" ve "PhoneNumber" sütunlarını içeren öğrencilerin aktif olduğu (IsActive=1) durumlarındaki verileri seçer. Görünüm, bir tablo gibi davranarak belirli bir sorguyu paylaşmak ve kullanmak için kullanışlıdır.

-- Object: Table [dbo].[Exams]: Bu bölümde, "Exams" tablosu için bir nesne (tablo) oluşturulması amaçlanmıştır. Ancak, verilen kod bloğunda "Exams" tablosunun tamamı eksik olduğu için tam bir tablo oluşturulmamıştır. Sadece bu kodun başlangıç aşaması yer almaktadır.

SET ANSI_NULLS ON ve SET QUOTED_IDENTIFIER ON: Bu iki komut, ANSI_NULLS ve QUOTED_IDENTIFIER seçeneklerini etkinleştirir. Bu, SQL Server'ın ANSI standartlarına uygun çalışmasını sağlar.

GO: "GO" ifadesi, SQL Server Management Studio gibi bazı SQL uygulamalarında bir sorgu yığınının bitişini belirtir ve SQL Server'a sorguyu yürütmesi için bir işaret verir.

Bu kod bloğu, veritabanını düzenleyen ve veri işlemlerini gerçekleştiren bir SQL betiğine benziyor. Ancak, "Exams" tablosunun tamamlayıcı kodları eksik olduğu için yarım bir yapıya sahiptir. Eğer "Exams" tablosu için daha fazla kod veya tanımlama yapmak istiyorsanız, eksik olan kısmı tamamlayabilir veya gerekli işlemleri ekleyebilirsiniz.
