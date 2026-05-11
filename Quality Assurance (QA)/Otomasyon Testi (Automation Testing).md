**Otomasyon Testi (Automation Testing) Nedir?**

Otomasyon testi, uygulamadaki test senaryolarının insanlar yerine araçlar ve scriptler tarafından otomatik çalıştırılmasıdır.Test planı yürütülürken manuel bir müdahaleye gerek kalmadan yapılan teste denir.

-Yani manuel testte bir kişinin yaptığı işlemleri: yazılmış test kodları,test frameworkleri,otomasyon araçları gerçekleştirir.

**Peki neden otomasyona ihtiyaç duyarız?**

- Tekrarlayan testleri hızlandırmak
- İnsan hatasını azaltmak
- Sürekli kalite kontrolü sağlamak
- Basit Mantık

**Manuel testte:**

_Tester uygulamayı açar → butona basar → sonucu kontrol eder_

**Otomasyon testinde:**

_Kod bunu otomatik yapar._

_Örnek:login ekranı_

-Manuel test:

- E-posta gir
- Şifre gir
- Giriş Yap’a bas
- Ana sayfa açıldı mı kontrol et

-Otomasyon testinde bunu bir script yapar:

`
 test("kullanıcı giriş yapabilmeli", async () => {
 
  await page.fill("#email", "test@gmail.com");
  
  await page.fill("#password", "123456");
  
  await page.click("#loginButton");

  await expect(page).toHaveURL("/home");
}); `

**Bu test:**

- Otomatik çalışır
- Defalarca tekrar edebilir
- İnsan müdahalesi istemez

