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
LevelId ile öğrencinin hangi lise kademesinde olduğunu (9,10,11 ve 12. sınıf),  
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

Bu tablomda Meslek rollerini belirledim.  
Yani meslek gruplarından öğretmen olanların içinden Müdür, Müdür Yardımcısı atadım ve ve diğerlerini de branş öğretmeni olarak rollendirdim.  

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

Okulda çalışan tüm meslek gruplarını bu tablomda tuttum.  
Ad-Soyad, mail adresi, telefon numarası,işe başlama tarihi gibi bilgileri kaydettim.  
IsActive ile de bu kişinin okulda halen çalışıp çalışmadığı bilgisini tuttum.  

CreatedProfessionId: Mesleği oluşturan kişinin Id'si  
CreatedDate: Meslek kaydının oluşturulduğu tarih ve saat bilgisi  
UpdatedProfessionId: Mesleği güncelleyen kişinin Id'si  
UpdatedDate: Meslek kaydının güncellendiği tarih ve saat bilgisini  

---

# Roles Table

```
Id
Name
IsActive
```

**AÇIKLAMA:**  

Bu tablodan çalışanların,  
Müdür, Müdür Yardımcısı ve Öğretmen atamalarını yaptım.  

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

Bu tablomda hangi konu başlığının hangi üniteye ait olduğunu belirledim.  
IsActive ile konunun müfredat içinde olup olmadığı bilgisini tuttum.  

CreatedProfessionId: Konuyu ekleyen kişinin Id'si  
CreatedDate: Konu kaydının oluşturulduğu tarih ve saat bilgisi  
UpdatedProfessionId: Konuyu güncelleyen kişinin Id'si  
UpdatedDate: Konu kaydının güncellendiği tarih ve saat bilgisi  

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

Bu tablomda her branşın ünitelerini müfredata göre belirledim.  
Bu ünitelerin hangi kademeye ve branşa ait olduğunu ve isimlerini ekledim.  
IsActive ile ünitenin müfredat içinde olup olmadığı bilgisini tuttum.  

CreatedProfessionId: Üniteyi ekleyen kişinin Id'si  
CreatedDate: Ünite kaydının oluşturulduğu tarih ve saat bilgisi  
UpdatedProfessionId: Üniteyi güncelleyen kişinin Id'si  
UpdatedDate: Ünite kaydının güncellendiği tarih ve saat bilgisi  

