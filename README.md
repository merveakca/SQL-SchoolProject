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
LevelId ile öğrencinin hangi lise kademesi olduğunu (9. sınıf, 10. sınıf gibi),  
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
Id
ProfessionId
BranchId
IsActive
```

**AÇIKLAMA:**  

Id: Meslek branşlarını benzersiz bir şekilde tanımlayan bir kimlik sütunu (Primary Key). Otomatik artan (IDENTITY), her yeni kayıt için bir öncekinden bir fazla değer alır ve boş bırakılamaz (NOT NULL).
ProfessionId: Meslek branşının bağlı olduğu mesleği belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki meslek bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).
BranchId: Meslek branşının bağlı olduğu ders branşını belirten sayısal bir değer (Foreign Key). Bu, başka bir tablodaki ders branşı bilgilerine bağlantı yapar ve boş bırakılamaz (NOT NULL).
IsActive: Meslek branşının aktif olup olmadığını belirten mantıksal bir değer (bit). Bu alan, meslek branşının kullanımda olup olmadığını gösterir. NULL değeri kabul edilebilir, yani meslek branşının aktiflik durumu belirtilmemiş olabilir.
Açıklamalar:
Bu tablo, meslekler ve bu mesleklerle ilişkilendirilmiş ders branşlarının yönetimi için kullanılabilir. Her bir kayıtta bir meslek branşı belirli bir mesleğe ve bir ders branşına atanır. Örneğin, "Doktor" mesleği "Tıp" ders branşıyla, "Mühendis" mesleği "Makine Mühendisliği" ders branşıyla ilişkilendirilebilir. Meslek branşlarının geçerli veya geçmiş durumları izlenebilir ve etkin olmayan meslek branşları arşivlenebilir. Bu tablo, eğitim kurumlarında, meslek odalarında ve benzeri alanlarda meslek ve ders branşlarının yönetimi için kullanışlı bir araçtır.

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


