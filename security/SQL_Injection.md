💉 **SQL Injection (SQLi)**, bir uygulamanın veritabanına gönderdiği SQL sorgularına kötü niyetli kod eklenmesiyle yapılan bir saldırı türüdür. Genellikle kullanıcıdan alınan veriler (giriş formu, arama kutusu vb.) yeterince kontrol edilmeden SQL sorgusuna eklenirse ortaya çıkar.

**_Mantığı Nedir?_**

Normalde uygulama şöyle bir sorgu çalıştırır:

`SELECT * FROM users 
WHERE email = 'eileen@test.com' 
AND password = '123456';`

Eğer uygulama kullanıcı girdisini doğrudan sorguya ekliyorsa saldırgan sorguyu değiştirebilir.Örneğin şifre alanına şu yazılırsa:

_' OR '1'='1_

Oluşan sorgu şuna dönüşebilir:

`SELECT * FROM users 
WHERE email = 'admin@mail.com'
AND password = '' OR '1'='1';`

'1'='1' her zaman doğru olduğu için giriş sistemi kandırılabilir.

❓**SQL Injection ile Neler Yapılabilir?**

Yetkiye bağlı olarak saldırgan:

Giriş sistemini bypass edebilir,kullanıcı verilerini okuyabilir,şifreleri çekebilir,verileri silebilir,admin yetkisi kazanabilir, tüm veritabanını bozabilir.

**SQL Injection Nasıl Oluşur?**

_En büyük sebep: ❌ Kullanıcı girdisini direkt SQL içine yazmak._

Örnek (tehlikeli kullanım):

const query = `
SELECT * FROM users 
WHERE email='${email}' 
AND password='${password}'
`;

Burada kullanıcı ne yazarsa sorgunun içine girer.

**Nasıl Korunulur?**

☑️1. Parameterized Query Kullanmak (En Önemlisi)

Kullanıcı verisini SQL stringine gömmek yerine parametre kullanılır.

✅ Güvenli örnek:

Node.js + MySQL
const query = `
SELECT * FROM users 
WHERE email = ? AND password = ?
`;

`db.query(query, [email, password]);`

Burada kullanıcı girdisi SQL kodu olarak değil veri olarak değerlendirilir.

☑️ _2. ORM Kullanmak_

ORM araçları çoğu zaman SQL Injection riskini azaltır.

Örnekler:

Prisma
Sequelize
TypeORM
Hibernate
Entity Framework

☑️ _3. Input Validation Yap_

**Kullanıcı girdisini kontrol et:**

_E-posta gerçekten e-posta mı?_
_Sayı alanına yazı girilmiş mi?_
_Maksimum karakter sınırı var mı?_

Örnek:

`if (!email.includes("@")) {
   return "Geçersiz email";
}`

☑️ _4. Yetkileri Kısıtla_

**_Veritabanı kullanıcısına gereksiz yetki verme._**

Örneğin login sistemi için kullanılan DB hesabı:

❌ DROP TABLE yetkisine sahip olmamalı.

☑️ _5. Hata Mesajlarını Gizle_

Şu tür hatalar saldırgana bilgi verir:

SQL syntax error near...

Kullanıcıya genel hata göster: Bir hata oluştu.Gerçek hata sadece loglarda tutulmalı.
