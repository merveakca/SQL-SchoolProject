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

Bu tabloda öğrenciye ait bilgileri tutmak istedim.  
LevelId ile öğrencinin hangi lise kademesi olduğunu (9,10,11 ve 12. sınıf),  
ClassId ile sınıfının şubesinin ne olduğunu (9-A, 10-B, gibi),  
öğrencinin adını ve soyadını kaydettim.  
Email adresini yazmasını zorunlu tuttum çünkü okul sistemine o adres ile girebilecek.  
Telefon numarasını null birakabilir çünkü her öğrencinin telefonu olmayabilir.  
Anne ve Baba adını alıp herhangi birisinin telefon numarasını yazmasını zorunlu tuttum.  
IsActive ile de öğrencinin kayıt durumunun aktifliğini belirledim  

CreatedProfessionId: Öğrencinin kaydını oluşturan kişinin Id'si  
CreatedDate: Kaydın oluşturulduğu tarihi ve saati  
UpdatedProfessionId: Son güncellemeyi yapan kişinin Id'si  
UpdatedDate: Son güncelleme tarihini ve saati  

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

Bu tabloda sınav bilgilerini tuttum;  
Hangi öğrencinin hangi sınıfta olduğunu ve hangi branştan sınava gireceğinin verisini aldım.  
Sınavın adını, (1. dönem 2. Fizik Sınavı gibi) hangi tarihte ve hangi saatte yapılacağı bilgisini tuttum.  
Ve öğrencinin sınav sonucunun verisini girdim. Burayı doldurmayı zorunlu tutmadım çünkü telafi sınavına girecek öğrencilerin not girişleri aynı tarihte yapılmayabilir.  
IsActive ile de sınavın aktif veya iptal durumunun bilgisini tuttum.  

CreatedProfessionId: sınav verilerini oluşturan kişinin kimlik Id'si  
CreatedDate: sınav verilerinin oluşturulduğu tarihi ve saati  
UpdatedProfessionId: sınav verilerini güncelleyen kişinin kimlik Id'si  
UpdatedDate: sınav verilerinin güncellendiği tarihi ve saati  

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

Bu tabloda, öğrencilerin ders programına göre, hangi branşın, hangi tarih ve saatinde sınıfta olup olmadıkları bilgisini tuttum.  
Tuttuğum bu verileri, öğrencilerimin performanslarının değerlendirilmesi ve derse devamının takibi gibi çeşitli analizler ve raporlar için de kullanabilirim.  

---

# Branches Table

```
Id
Name
IsActive
```

**AÇIKLAMA:**  

Bu tablomda lise kademesinde verilebilecek branşların bilgisini tuttum (Fizik, Kimya, Biyoloji, Matematik, Edebiyat...).  
IsActive ile de herhangi bir dersin okulda verilip verilmediğini belirttim  

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

Bu tablomda sınıfların herbirinin kademesini (9,10,11 ve 12. sınıf) belirleyerek, her bir sınıfa bir danışman öğretmen atadım.  
Sınıf isimlerini belirledim (9-A, 9-B, 10-A gibi).  
IsActive ile de sınıfın aktif olup olmadığını belirttim.  
  
CreatedProfessionId: sınıfı oluşturan kullanıcının Id'si  
CreatedDate: Sınıfın oluşturulduğu tarih ve saat bilgisi  
UpdatedProfessionId: sınıf bilgisini güncelleyen kullanıcının Id'si  
UpdatedDate: Sınıfın güncellendiği tarih ve saat bilgisi  

---

# LessonPrograms Table

```
Id
BranchId
Date
IsActive
```

**AÇIKLAMA:**  

Bu tablomda hangi dersin hangi tarih ve saatte yapılacağı bilgisini tuttum.
IsActive ile de ders programının aktif olup olmadığını belirttim

---

# Levels Table

```
Id
Name
IsActive
```

**AÇIKLAMA:**  

Bu tablomu, sınıf kademeleri için tasarladım (9,10,11 ve 12. sınıf).
Birçok tablo ile de ilişkili kullandım.

---

# ProfessionBranch Table

```
Id
ProfessionId
BranchId
IsActive
```

**AÇIKLAMA:**  

Bu tablomda, okul içinde çalışan meslek gruplarına branş ataması yaptım.
Yani Müdür ya da Müdür Yardımcısının ve diğer tüm öğretmenlerin branşı olmak zorunda olduğunu düşenerek oluşturdum.
Bu meslek grupları dışında çalışan kişilere bu atamayı yapmadım (kat görevlisi, güvenlik, kantin görevlisi...).

---

# ProfessionRoles Table

```
Id
ProfessionId
RoleId
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:**  

Id: Meslek rollerini benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY), her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).

ProfessionId: Meslek rollerinin bağlı olduğu mesleği belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).

RoleId: Meslek rollerini belirleyen sayısal bir değer (Foreign Key). Bu, başka bir tablodaki rol bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).

IsActive: Meslek rollerinin aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, meslek rollerinin kullanımda olup olmadığını gösterir. NULL değeri kabul edilebilir, yani meslek rollerinin aktiflik durumu belirtilmemiş olabilir.

CreatedProfessionId: Meslek rolü oluşturulduğunda ilişkilendirilen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek oluşturulduğunda bu alan doldurulabilir.

CreatedDate: Meslek rolünün oluşturulduğu tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Meslek rolünün ne zaman oluşturulduğunu kaydetmek için kullanılır.

UpdatedProfessionId: Meslek rolü güncellendiğinde ilişkilendirilen güncellenen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek güncellendiğinde bu alan doldurulabilir.

UpdatedDate: Meslek rolünün güncellendiği tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Meslek rolünün ne zaman güncellendiğini kaydetmek için kullanılır. Bu alan, meslek rolü güncellendiğinde otomatik olarak güncellenir.

---

# Professions Table

```
Id
Name
Surname
Email
PhoneNumber
DateOfStart
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:**  

Id: Meslekleri benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY) olduğu için her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).

Name: Mesleğin adını tutan metinsel (nvarchar) bir alan. Meslek adları, en fazla 50 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).

Surname: Meslek mensuplarının soyadını tutan metinsel (nvarchar) bir alan. Soyadları, en fazla 50 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).

Email: Meslek mensuplarının e-posta adresini tutan metinsel (nvarchar) bir alan. E-posta adresleri, en fazla 100 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).

PhoneNumber: Meslek mensuplarının telefon numarasını tutan metinsel (nvarchar) bir alan. Telefon numaraları, 11 karakter uzunluğunda olmalıdır ve boş bırakılamaz (NOT NULL).

DateOfStart: Meslek mensuplarının mesleğe başladığı tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Meslek mensuplarının ne zaman mesleğe başladığını kaydetmek için kullanılır ve boş bırakılamaz (NOT NULL).

IsActive: Meslek kaydının aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, meslek mensubunun aktif olup olmadığını gösterir. NULL değeri kabul edilebilir, yani meslek kaydının aktiflik durumu belirtilmemiş olabilir.

CreatedProfessionId: Meslek oluşturulduğunda ilişkilendirilen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek oluşturulduğunda bu alan doldurulabilir.

CreatedDate: Meslek kaydının oluşturulduğu tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Meslek kaydının ne zaman oluşturulduğunu kaydetmek için kullanılır.

UpdatedProfessionId: Meslek güncellendiğinde ilişkilendirilen güncellenen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek güncellendiğinde bu alan doldurulabilir.

UpdatedDate: Meslek kaydının güncellendiği tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Meslek kaydının ne zaman güncellendiğini kaydetmek için kullanılır. Bu alan, meslek kaydı güncellendiğinde otomatik olarak güncellenir.

---

# Roles Table

```
Id
Name
IsActive
```

**AÇIKLAMA:**  

Id: Rollerin benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY) olduğu için her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).

Name: Rolün adını tutan metinsel (nvarchar) bir alan. Rol adları, en fazla 50 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).

IsActive: Rolün aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, rolün kullanımda olup olmadığını gösterir. NULL değeri kabul edilebilir, yani rolün aktiflik durumu belirtilmemiş olabilir.

---

# Topics Table

```
Id
UnitId
Name
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:**  

Bu tablo, ders üniteleriyle ilişkilendirilmiş konu bilgilerini saklamak için kullanılan bir veritabanı tablosudur. Her bir konu için aşağıdaki alanları içerir:

Id: Konuları benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY) olduğu için her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).

UnitId: Konunun bağlı olduğu ders ünitesini belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki ders ünite bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).

Name: Konunun adını tutan metinsel (nvarchar) bir alan. Konu adları, en fazla 50 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).

IsActive: Konunun aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, konunun kullanımda olup olmadığını gösterir. NULL değeri kabul edilebilir, yani konunun aktiflik durumu belirtilmemiş olabilir.

CreatedProfessionId: Konu oluşturulduğunda ilişkilendirilen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek oluşturulduğunda bu alan doldurulabilir.

CreatedDate: Konu kaydının oluşturulduğu tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Konunun ne zaman oluşturulduğunu kaydetmek için kullanılır.

UpdatedProfessionId: Konu güncellendiğinde ilişkilendirilen güncellenen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek güncellendiğinde bu alan doldurulabilir.

UpdatedDate: Konu kaydının güncellendiği tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Konunun ne zaman güncellendiğini kaydetmek için kullanılır. Bu alan, konu kaydı güncellendiğinde otomatik olarak güncellenir.

---

# Units Table

```
Id
LevelId
BranchId
Name
IsActive
CreatedProfessionId
CreatedDate
UpdatedProfessionId
UpdatedDate
```

**AÇIKLAMA:**  

Bu tablo, ders birimleriyle ilişkilendirilmiş bilgileri saklamak için kullanılan bir veritabanı tablosudur. Her bir ders birimi için aşağıdaki alanları içerir:

Id: Ders birimlerini benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY) olduğu için her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).

LevelId: Ders biriminin bağlı olduğu eğitim seviyesini belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki eğitim seviyesi bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).

BranchId: Ders biriminin bağlı olduğu ders branşını belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki ders branşı bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).

Name: Ders biriminin adını tutan metinsel (nvarchar) bir alan. Ders birimi adları, en fazla 50 karakter uzunluğunda olabilir ve boş bırakılamaz (NOT NULL).

IsActive: Ders biriminin aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, ders biriminin kullanımda olup olmadığını gösterir. NULL değeri kabul edilebilir, yani ders biriminin aktiflik durumu belirtilmemiş olabilir.

CreatedProfessionId: Ders birimi oluşturulduğunda ilişkilendirilen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek oluşturulduğunda bu alan doldurulabilir.

CreatedDate: Ders birimi kaydının oluşturulduğu tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Ders biriminin ne zaman oluşturulduğunu kaydetmek için kullanılır.

UpdatedProfessionId: Ders birimi güncellendiğinde ilişkilendirilen güncellenen meslek kimlik numarasını tutan sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar. İlgili meslek güncellendiğinde bu alan doldurulabilir.

UpdatedDate: Ders birimi kaydının güncellendiği tarih ve saat bilgisini içeren bir zaman damgası (datetime) alanı. Ders biriminin ne zaman güncellendiğini kaydetmek için kullanılır. Bu alan, ders birimi kaydı güncellendiğinde otomatik olarak güncellenir.


