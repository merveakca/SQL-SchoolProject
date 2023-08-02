# SQL-SchoolProject
# DataBase'imde Oluşturduğum Tablolarım ve Açıklamalarım
# "My created database tables and their descriptions"
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

Id: yapılan yoklamanın kimlik numarasıdır  
LessonProgramId: ders programını tanımlar  
StudentId: derse katılan öğrenciyi tanımlar  
LessonTime: yoklamanın yapıldığı dersin tarih ve saat bilgisini içerir  
IsInClass: öğrencinin ders saatlerinde sınıfta olup olmadığını belirtir  
IsActive: yapılan yoklamanın aktif olup olmadığını belirtir  

**Notlar**  

Bu tablo, öğrencilerin devam durumlarını ve katılımlarını izlemek için kullanılabilir. Örneğin, belirli bir tarihte hangi öğrencilerin derste olduğunu veya devamsız olduğunu belirlemek için kullanılabilir. Bu veriler, öğrenci performansının değerlendirilmesi ve öğrenci katılımının takibi gibi çeşitli analizler ve raporlar için de kullanılabilir.

---

# Branches Table

```
Id
Name
IsActive
```

**AÇIKLAMA:**  

Id: branşın kimlik numarasıdır  
Name: Ders branşının adını tutar (Fizik, Kimya, Biyoloji, Matematik, Edebiyat...)  
IsActive: dersin okulda verilip verilmediğini belirler  

**Notlar**  

Bu tablo, bir eğitim kurumunda veya ders programı yönetim sisteminde kullanılarak derslerin farklı branşlara ayrılmasını ve bu branşlarla ilişkilendirilmesini sağlar. Örneğin, Matematik, Fen Bilimleri, Edebiyat gibi ders branşları bu tabloda kaydedilebilir. Ayrıca, ders programlarının oluşturulması ve derslerin bu branşlara göre planlanması için kullanılabilir.

---

# Classes Table

```
Id
LevelId
ProfessionBranchId
Name
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:**  

Id: sınıfların benzersiz kimlik numaralarıdır  
LevelId: Levels tablosu ile ilişkilidir, sınıfın kademesini belirler (9.sınıf, 10.sınıf,11.sınıf ve 12.sınıf)  
ProfessionBranchId: sınıfın danışman öğretmeninin atandığı yerdir  
Name: sınıfın adını tutar (9-A, 9-B, 10-A gibi)  
IsActive: Sınıfın aktif olup olmadığını belirtir  
CreatedProfessionId: sınıfı oluşturan kullanıcının Id'sidir  
CreatedDate: Sınıfın oluşturulduğu tarih ve saat bilgisidir  
UpdatedProfessionId: sınıf bilgisini güncelleyen kullanıcının Id'sidir  
UpdatedDate: Sınıfın güncellendiği tarih ve saat bilgisidir  

---

# LessonPrograms Table

```
Id
BranchId
Date
IsActive
```

**AÇIKLAMA:**  

Id: Ders programlarını benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY), her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).
BranchId: Ders programının bağlı olduğu ders branşını belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki ders branşı bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).
Date: Ders programının yapılacağı tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Bu alan, ders programının ne zaman gerçekleşeceğini belirtmek için kullanılır ve boş bırakılamaz (NOT NULL).
IsActive: Ders programının aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, ders programının geçerli olup olmadığını gösterir. NULL değeri kabul edilebilir, yani ders programının aktiflik durumu belirtilmemiş olabilir.
Bu tablo, bir eğitim kurumunda veya ders yönetim sisteminde kullanılarak ders programlarını yönetmek ve takip etmek için kullanılabilir. Her bir ders programı, belirli bir ders branşına ait olacak şekilde düzenlenir ve programın gerçekleşeceği tarih ve saat bilgisi tutulur. Ders programlarının geçmiş ve gelecek tarihlerine göre filtreleme yapılabilir ve ders programlarına ilişkin güncel bilgilerin takibi sağlanabilir.

---

# Levels Table

```
Id
Name
IsActive
```

**AÇIKLAMA:**  

Id: Seviyeleri benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY), her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).
Name: Eğitim seviyesinin adını tutan metinsel (nvarchar) bir alan. Seviye adları, en fazla 50 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).
IsActive: Seviyenin aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, seviyenin kullanımda olup olmadığını gösterir. NULL değeri kabul edilebilir, yani seviyenin aktiflik durumu belirtilmemiş olabilir.
Bu tablo, bir eğitim kurumunda veya ders yönetim sisteminde kullanılarak farklı eğitim seviyelerinin (örneğin, ilkokul, ortaokul, lise) yönetimini sağlar. Her bir seviye, belirli bir eğitim düzeyine veya sınıf düzeyine ait olacak şekilde kaydedilir ve seviyelere göre filtreleme ve sınıflandırma yapılabilir. Ayrıca, seviyelerin geçmiş ve gelecek dönemlerine göre takibi ve yönetimi bu tablo üzerinden yapılabilir.

---

# ProfessionBranch Table

```

```

**AÇIKLAMA:**  

---

# ProfessionRoles Table

```

```

**AÇIKLAMA:**  

---

# Professions Table

```

```

**AÇIKLAMA:**  

---

# Roles Table

```

```

**AÇIKLAMA:**  

---

# Topics Table

```

```

**AÇIKLAMA:**  

---

# Units Table

```

```

**AÇIKLAMA:**  

