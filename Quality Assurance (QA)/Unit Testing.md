**Unit Test Nedir?**

🎲Unit test, yazılımın en küçük parçalarının (fonksiyon, method, component) otomatik olarak test edilmesidir.Genellikle geliştiriciler yazar.

**Amaç:**

- Kodun doğru çalıştığını doğrulamak
- Yeni kod eklenince eski yapının bozulmadığını kontrol etmek.

**_Unit Test Örneği_**
  
` function topla(a, b) {
  return a + b;
} `


**Unit test:**

`test("2 + 3 = 5", () => {
  expect(topla(2,3)).toBe(5);
});`

**Bu test:**

- Otomatik çalışır.
- İnsan müdahalesi istemez.
- Kodun doğru çalışıp çalışmadığını kontrol eder.

**➕Unit Testin Avantajları**
- Çok hızlıdır
- Otomatiktir
- Kod kalitesini artırır
- Refactor işlemlerini güvenli hale getirir
- Bug’ları erken yakalar
  
**➖Dezavantajları**
- Yazması zaman ister
- Sadece küçük kod parçalarını test eder
- Gerçek kullanıcı deneyimini test etmez

