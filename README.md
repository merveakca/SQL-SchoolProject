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

Id: kimlik numarasıdır 
LevelId: lise kademesidir (9. sınıf, 10. sınıf gibi)  
ClassId: sınıfın şubesidir (9-A, 10-B, gibi)  
Name: öğrencinin adıdır  
Surname: öğrencinin soyadıdır  
Email: öğrenciye ait olan e-posta adresinidir. Null olamaz çünkü sisteme mail adresi ile giriş yapılacaktır  
PhoneNumber: öğrencinin telefon numarasıdır 
MotherName: Öğrencinin annesinin adını temsil eder  
FatherName: Öğrencinin babasının adını temsil eder  
ParentPhoneNumber: Öğrencinin velisinin telefon numarasını temsil eder ve null olamaz, iletişim için zorunludur  
IsActive: Öğrencinin okula kayıt durumunun devam edip etmediğini temsil eder  
CreatedProfessionId: Öğrencinin kaydını oluşturan kişinin Id'sini temsil eder  
CreatedDate: Kaydın oluşturulduğu tarihi ve saati temsil eden değer  
UpdatedProfessionId: Son güncellemeyi yapan kişinin Id'sini temsil eder  
UpdatedDate: Son güncelleme tarihini ve saatini temsil eder  

**Notlar**  

Bu tablo, öğrencilerin temel bilgilerini içeren verileri saklamak için tasarlanmıştır.  
CreatedProfessionId ve UpdatedProfessionId sütunları, verilerin oluşturulduğu ve güncellendiği meslek kimlik numaralarını ilişkilendirmek için kullanılabilir.  
CreatedDate ve UpdatedDate sütunları, verilerin oluşturulma ve güncellenme zamanlarını saklamak için kullanılabilir.  
PhoneNumber sütunu opsiyoneldir, çünkü bazı öğrencilerin telefon numaraları olmayabilir.  
Bu tabloyu kullanarak, öğrencilere ilişkin verileri kolayca saklayabilir ve yönetebilirsiniz.  

---

# Exams Table

```
Id
StudentId
ClassId
BranchId
Name
Note
ExamDate
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:** 

Exams Tablosu, aşağıdaki sütunları içermektedir: 

Id: sınavların kimlik numarasıdır  
StudentId: bu alan, Students tablosuyla ilişkilendirilmiş olup, hangi öğrencinin hangi sınavı aldığını belirlemek için kullanılacaktır  
ClassId: bu alan da Classes tablosuyla ilişkilendirilmiş olup, hangi sınıfın hangi sınavı aldığını belirlemek için kullanılacaktır  
BranchId: sınavın düzenlendiği şubenin kimlik numarasını temsil eder. Şubeler, okulların farklı yerlerinde veya farklı binalarında olabilir ve bu alan, hangi şubenin hangi sınavı düzenlediğini belirlemek için kullanılacaktır  
Name: sınavın adını temsil eder, örneğin "1. Dönem 1. Matematik Yazılı Sınavı" veya "2. Dönem 2. Fizik Yazılı Sınavı" gibi  
Note: sınav sonucunda alınan notu temsil eder  
ExamDate: sınavın yapıldığı tarihi ve saati temsil eder. Null olabilir, çünkü sınava giremeyip telafiye katılacak öğrenciler de olacaktır  
IsActive: sınavın geçerli yada iptal olup olmadığını belirler  
CreatedProfessionId: sınav verilerini oluşturan kişinin kimlik Id'sini tutar  
CreatedDate: sınav verilerinin oluşturulduğu tarihi ve saati temsil eder  
UpdatedProfessionId: sınav verilerini güncelleyen kişinin kimlik Id'sini tutar  
UpdatedDate: sınav verilerinin güncellendiği tarihi ve saati temsil eder  

Bu tablo, öğrenci sınavlarının bilgilerini saklamak ve bu bilgilere ilişkin ilişkili diğer tablolarla bağlantı kurmak için kullanılabilir. Örneğin, bu tabloyu öğrenci bilgileri ve sınıf bilgileri tablolarıyla ilişkilendirerek, belirli bir öğrencinin hangi sınavı aldığını ve bu sınavda aldığı notu kolayca bulabilirsiniz.

---

# Attendance Table

```
Id
LessonProgramId
StudentId
LessonTime
IsInClass
IsActive
```

**AÇIKLAMA:**  

Attendance Tablosu, aşağıdaki sütunları içermektedir:  

Id: Katılım kayıtlarının kimlik numarasıdır  
LessonProgramId: Katılımın kaydedildiği ders programını tanımlar  
StudentId: Katılımın kaydedildiği öğrenciyi tanımlar  
LessonTime: Katılımın kaydedildiği tarih ve saat bilgisini içerir
IsInClass: Bir öğrencinin ders saatlerinde sınıfta olup olmadığını belirtir  
IsActive: Katılım kaydının aktif olup olmadığını belirtir  

**Notlar**  

Bu tablo, öğrencilerin devam durumlarını ve katılımlarını izlemek için kullanılabilir. Örneğin, belirli bir tarihte hangi öğrencilerin derste olduğunu veya devamsız olduğunu belirlemek için kullanılabilir. Bu veriler, öğrenci performansının değerlendirilmesi ve öğrenci katılımının takibi gibi çeşitli analizler ve raporlar için de kullanılabilir.
