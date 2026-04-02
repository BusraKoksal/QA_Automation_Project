🚀 API Test Automation Suite: Postman & JavaScript
Bu proje, modern yazılım test metodolojilerini uygulamak ve backend servislerinin stabilitesini doğrulamak amacıyla geliştirilmiştir. Proje kapsamında, gerçek zamanlı çalışan API'ler üzerinden bir verinin oluşturulmasından silinmesine kadar geçen tüm CRUD süreçleri otomatize edilmiştir.

🛠 Kullanılan Servisler ve Senaryolar
Test süreçlerinde iki farklı API yapısı üzerinden farklı senaryolar kurgulanmıştır:

🎯 --JSONPlaceholder (Blog Yönetim Sistemi)--
    Amacı: Bir içerik yönetim sisteminin backend yapısını test etmek.
    Kullanılan Endpoint: https://jsonplaceholder.typicode.com/posts/1
    Bu sistemin backend operasyonlarını simüle etmek amacıyla Full CRUD Lifecycle uygulanmıştır:
       POST: Yeni bir içerik oluşturma ve 201 Created doğrulaması.
       GET: Oluşturulan verinin doğruluğunu sorgulama.
       PUT: Mevcut veriyi güncelleyerek sistemin tutarlılığını test etme.
       DELETE: Test verilerini temizleme ve başarılı silme onayı.

🎯 --The Cat API (Dinamik Medya Servisi)--
    Amacı: Dinamik veri dönen (rastgele resim) servislerin doğrulanması.
    Kullanılan Endpoint: https://api.thecatapi.com/v1/images/search
    Test Edilen Veri: Gelen JSON verisinin liste formatında olup olmadığı ve geçerli bir resim URL'i içerip içermediği.

Adım Adım Uygulanan Test Senaryoları
Her bir istek (Request) için özelleştirilmiş JavaScript tabanlı otomasyon scriptleri yazılmıştır:

1️⃣ HTTP Status Code & Metot Kontrolü
Her işlemin doğasına uygun yanıt kodu dönüp dönmediği doğrulanmıştır.

JavaScript
pm.test("İşlem Başarılı: Status Code Kontrolü", function () {
    pm.expect(pm.response.code).to.be.oneOf([200, 201]);
});

2️⃣ Veri Bütünlüğü ve Şema Doğrulama (Data Integrity)
Gelen yanıtın beklenen anahtarları (id, title, body, userId) içerip içermediği ve veri tiplerinin doğruluğu Assertion metotları ile denetlenmiştir. Özellikle PUT işleminden sonra verinin gerçekten güncellendiği teyit edilmiştir.

3️⃣ Performans (Response Time) Testi
Yüksek ölçekli sistemlerde servis hızı kritiktir. Tüm isteklerin 500ms altında yanıt vermesi bir kabul kriteri olarak belirlenmiş ve test edilmiştir.

JavaScript
pm.test("Performans Testi: Yanıt süresi 500ms altında", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

🐞 Karşılaşılan Zorluklar ve Hata Ayıklama (Debugging)
Proje geliştirme aşamasında karşılaşılan "Empty Request URL" gibi konfigürasyon hataları; Postman konsol logları ve Postman Runner çıktıları incelenerek çözülmüştür. Bu süreç, test süreçlerinde log takibi ve root-cause (kök neden) analizi yapma yetkinliğini pekiştirmiştir.

✍️ Teknik Makale ve Detaylı Anlatım
Bu projenin hazırlık aşamaları ve API test otomasyonunun teknik detayları hakkında kaleme aldığım makaleme buradan ulaşabilirsiniz:
👉 Medium: Backend'in Kalp Atışlarını Dinlemek: Postman ile API Test Süreçleri

📊 Test Sonuçları (Postman Runner)
Aşağıdaki görselde, tüm CRUD operasyonlarının ve dinamik servis testlerinin tek seferde (Batch Run) hatasız çalıştığı ve tüm senaryoların başarıyla geçtiği (PASSED) görülmektedir.

![Test Sonuçları](test-result.png)




