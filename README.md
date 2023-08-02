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

*Id:* Öğrenci kimlik numarasını temsil eden benzersiz bir tamsayı değeridir  
*LevelId:* Öğrencinin lise kademesini belirler (9. sınıf, 10. sınıf gibi)  
*ClassId:* Öğrencinin sınıfını şubesi ile belirler (9-A, 10-B, gibi)  
*Name:* Öğrencinin adını temsil eder  
*Surname:* Öğrencinin soyadını temsil eder  
*Email:* Öğrencinin e-posta adresini temsil eder. Null olamaz çünkü sisteme mail adresi ile giriş yapılacaktır  
*PhoneNumber:* Öğrencinin telefon numarasını temsil eder. Null olabilir. Çünkü her öğrencinin numarası olmayabilir  
*MotherName:* Öğrencinin annesinin adını temsil eder  
*FatherName:* Öğrencinin babasının adını temsil eder  
*ParentPhoneNumber:* Öğrencinin velisinin telefon numarasını temsil eder ve null olamaz, iletişim için zorunludur  
*IsActive:* Öğrencinin okula kayıt durumunun devam edip etmediğini temsil eder  
*CreatedProfessionId:* Öğrencinin kaydını oluşturan kişinin Id'sini temsil eder  
*CreatedDate:* Kaydın oluşturulduğu tarihi ve saati temsil eden değer  
*UpdatedProfessionId:* Son güncellemeyi yapan kişinin Id'sini temsil eder  
*UpdatedDate:* Son güncelleme tarihini ve saatini temsil eder  

**Notlar**  

Bu tablo, öğrencilerin temel bilgilerini içeren verileri saklamak için tasarlanmıştır.  
IsActive sütunu, öğrencinin etkin veya pasif olduğunu belirtmek için kullanılabilir.  
CreatedProfessionId ve UpdatedProfessionId sütunları, verilerin oluşturulduğu ve güncellendiği meslek kimlik numaralarını ilişkilendirmek için kullanılabilir.  
CreatedDate ve UpdatedDate sütunları, verilerin oluşturulma ve güncellenme zamanlarını saklamak için kullanılabilir.  
PhoneNumber sütunu opsiyoneldir, çünkü bazı öğrencilerin telefon numaraları olmayabilir.  
Bu tabloyu kullanarak, öğrencilere ilişkin verileri kolayca saklayabilir ve yönetebilirsiniz.  


```

```
