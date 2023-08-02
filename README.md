# SQL-SchoolProject
---
# Students Table
```
Id
LevelId
ClassId
Name
Surname
Email
PhoneNumber
MotherName
FatherName
ParentPhoneNumber
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:**  

Students Tablosu, aşağıdaki sütunları içermektedir:  

*Id:* Öğrenci kimlik numarasını temsil eden benzersiz bir tamsayı değeri.  
*LevelId:* Öğrencinin lise kademesini belirler (9. sınıf, 10. sınıf...)  
*ClassId:* Öğrencinin sınıfını belirler
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

Object: Table [dbo].[Exams]: Bu bölümde, "Exams" tablosu için bir nesne (tablo) oluşturulması amaçlanmıştır. Ancak, verilen kod bloğunda "Exams" tablosunun tamamı eksik olduğu için tam bir tablo oluşturulmamıştır. Sadece bu kodun başlangıç aşaması yer almaktadır.

SET ANSI_NULLS ON ve SET QUOTED_IDENTIFIER ON: Bu iki komut, ANSI_NULLS ve QUOTED_IDENTIFIER seçeneklerini etkinleştirir. Bu, SQL Server'ın ANSI standartlarına uygun çalışmasını sağlar.

GO: "GO" ifadesi, SQL Server Management Studio gibi bazı SQL uygulamalarında bir sorgu yığınının bitişini belirtir ve SQL Server'a sorguyu yürütmesi için bir işaret verir.

