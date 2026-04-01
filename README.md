🚀 API Test Automation Suite: Postman & JavaScript
  Bu proje, modern yazılım test metodolojilerini uygulamak ve backend servislerinin stabilitesini doğrulamak amacıyla geliştirilmiştir. Proje kapsamında gerçek       zamanlı çalışan halka açık API'ler kullanılarak test senaryoları kurgulanmıştır.

🛠 Kullanılan Servisler ve Veri Kaynakları
  Test süreçlerinde aşağıdaki iki farklı servis simüle edilmiştir:

🎯 --JSONPlaceholder (Blog Servisi)--
  Amacı: Bir içerik yönetim sisteminin backend yapısını test etmek.
  Kullanılan Endpoint: https://jsonplaceholder.typicode.com/posts/1
  Test Edilen Veri: 1 numaralı postun başlığı, içeriği ve kullanıcı ID'si.

🎯 --The Cat API (Görsel Servisi)--
  Amacı: Dinamik veri dönen (rastgele resim) servislerin doğrulanması.
  Kullanılan Endpoint: https://api.thecatapi.com/v1/images/search
  Test Edilen Veri: Gelen JSON verisinin liste formatında olup olmadığı ve geçerli bir resim URL'i içerip içermediği.

🧪 Adım Adım Uygulanan Test Senaryoları
  Her bir istek (Request) için aşağıdaki JavaScript tabanlı otomasyon scriptleri yazılmıştır:
  1. HTTP Status Code Kontrolü
  Servisin çalışır durumda olup olmadığını anlamak için 200 OK veya 201 Created yanıtları doğrulanmıştır.

💻 JavaScript
  pm.test("Status code is 200", function () {
      pm.response.to.have.status(200);
  });

2. Veri Bütünlüğü ve Şema Doğrulama
  Gelen yanıtın (JSON) beklenen anahtarları (id, title, url) içerip içermediği ve dönen değerlerin veri tipi doğruluğu kontrol edilmiştir.

3. Performans (Response Time) Testi
   Yüksek trafikli sistemlerde hız kritiktir. Bu nedenle yanıt süresinin 500ms altında olması şartı aranmış ve doğrulanmıştır.

🐞 Karşılaşılan Zorluklar ve Hata Ayıklama (Debugging)
  Projenin geliştirme aşamasında "Empty Request URL" hatası ile karşılaşılmış; Postman konsol logları ve Postman Runner çıktıları incelenerek konfigürasyon           eksikliği giderilmiştir. Bu süreç, test süreçlerinde log takibi ve root-cause (kök neden) analizi yapma yetkinliğini pekiştirmiştir.

📊 Test Sonuçları (Postman Runner)
✅ Aşağıdaki görsellerde, tüm koleksiyonun tek seferde (Batch Run) hatasız bir şekilde çalıştığı ve tüm senaryoların başarıyla geçtiği (PASSED) görülmektedir.




