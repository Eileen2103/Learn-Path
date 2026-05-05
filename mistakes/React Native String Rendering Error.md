🎯Hata Başlığı (Issue Title)
Invariant Violation: Text strings must be rendered within a <Text> component.

-Hata Açıklaması (Description)
React Native uygulamasında yeni bir sayfa (personal_details.tsx) oluşturulurken, sayfa render edildiği sırada uygulama çökmekte ve "Text strings must be rendered within a <Text> component" hatası fırlatılmaktadır.

-Hata Nedeni (Root Cause)
React Native, web tabanlı React'ten farklı olarak, bir <View> veya başka bir layout bileşeni içinde doğrudan metin barındırılmasına izin vermez. Hata şu iki nedenden kaynaklanmıştır:

👻Görünmez Karakterler: JSX bloğu içerisinde { } süslü parantezlerin dışında kalan yanlışlıkla bırakılmış boşluklar, virgüller veya satır sonu karakterleri.

✍️Yorum Satırı Karmaşası: JSX içerisindeki `` yorum satırlarının etrafındaki boşlukların, render motoru tarafından "çıplak metin" (naked string) olarak algılanması.

☑️Çözüm (Solution)
Hatanın çözümü için return bloğu içerisindeki tüm metin tabanlı veriler ve değişkenler sıkı bir kontrolden geçirilmiştir.Metin Sarmalama: Tüm değişkenler (Örn: {user?.name}) mutlaka bir <Text> etiketi içine alınmıştır.Güvenli Operatör Kullanımı: Boş veri gelmesi durumunda render motorunun şaşırmaması için Nullish Coalescing (??) veya Logical OR (||) operatörleri kullanılarak boş string ('') dönmesi sağlanmıştır.

Hatalı: {user?.name} (View içinde doğrudan kullanımda riskli)

Doğru: <Text>{user?.name ?? ''}</Text>

⭐ JSX Temizliği: JSX blokları arasındaki gereksiz boşluklar ve render'ı tetikleyebilecek yorum satırları temizlenmiştir.
