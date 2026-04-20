🌍 3D Flight Simulation & Geospatial Data Management
Bu proje; ASP.NET MVC mimarisi üzerine kurulu, CesiumJS kütüphanesi ile 3D harita görselleştirmesi sunan ve uçuş simülasyonu gerçekleştiren kapsamlı bir Coğrafi Bilgi Sistemi (CBS) uygulamasıdır. Kullanıcılar, 3D modelleri (.glb) harita üzerinde konumlandırabilir, karmaşık rotalar oluşturabilir ve bu süreçlerin sonunda raporlar alabilirler.

🌟 Ana Özellikler
3D Model Entegrasyonu: .glb formatındaki 3D modelleri koordinat (Lat/Lon/Alt) ve eğim (Pitch) bilgileriyle haritaya ekleme.

Dinamik Uçuş Simülasyonu: Belirlenen rotalar üzerinde, hız ve irtifa verilerine bağlı olarak nesnelerin 3D simülasyonu.

Rota ve Durak Yönetimi: Nesnelere özel rota verileri atama ve simülasyon duraklarını gerçek zamanlı takip etme.

Otomatik Raporlama: Tamamlanan simülasyonlar için PDF, Excel ve Word formatlarında uçuş raporu (ortalama hız, mesafe, irtifa vb.) oluşturma.

Gelişmiş CMS Paneli: Harita nesnelerinin görünürlüğünü, konumunu ve modellerini yönetmek için kullanıcı dostu arayüz.

🛠️ Teknik Altyapı
Backend: ASP.NET MVC, C# (.NET Framework 4.7.2).

Veritabanı: PostgreSQL (Npgsql sürücüsü ile asenkron yönetim).

Harita Motoru: CesiumJS (3D Globe Rendering).

Frontend: JavaScript (ES6+), jQuery, Bootstrap, CSS3.

Raporlama Araçları: html2pdf, XLSX.js, html-to-docx, PDF.js.

📁 Veri Modelleri
HaritaNesnesi: Nesnenin adı, koordinatları, 3D dosya yolu ve görünürlük durumunu tutar.

HaritaNesnesiRota: Rota isimlerini ve rotaya ait koordinat dizilerini (JSON formatında) saklar.

⚙️ Kurulum ve Başlatma
1. Veritabanı Yapılandırması
PostgreSQL üzerinde aşağıdaki tabloları oluşturun:

SQL
CREATE TABLE harita_nesneleri (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    lat DOUBLE PRECISION,
    lon DOUBLE PRECISION,
    alt DOUBLE PRECISION,
    pitch DOUBLE PRECISION,
    glb_file TEXT,
    isvisible BOOLEAN DEFAULT TRUE,
    "RotaId" INTEGER
);

CREATE TABLE harita_nesneleri_rota (
    "RotaId" SERIAL PRIMARY KEY,
    "RotaAdi" VARCHAR(255),
    "RouteData" TEXT
);
2. Uygulama Ayarları
Web.config dosyasındaki PostgreConnection bağlantı dizesini kendi veritabanı bilgilerinizle güncelleyin.

3D Model Dizini: Proje ana dizininde ~/Models/3D/ klasörünün yazma izinlerine sahip olduğundan emin olun.

NuGet Paketleri: Visual Studio üzerinden paketleri restore edin (Npgsql ve Newtonsoft.Json otomatik yüklenecektir).

🚀 Gelecek Geliştirmeler ve Teknik Yol Haritası
Projenin mevcut sürümü temel fonksiyonları başarıyla yerine getirmekle birlikte, gelecek versiyonlarda aşağıdaki iyileştirmelerin yapılması planlanmaktadır:

Mimari Dönüşüm: Veri erişim katmanında kullanılan ham SQL sorgularının, projede hali hazırda tanımlı olan Entity Framework yapısına tam entegrasyonu.

Güvenlik: Web.config dosyasındaki hassas verilerin (bağlantı dizeleri vb.) ortam değişkenlerine (Environment Variables) taşınması.

Kod Modülerliği: Tek dosya üzerinde toplanan yoğun frontend (JavaScript/HTML) kodunun, modern UI bileşenlerine ayrıştırılması.

Hata Yönetimi: Uygulama genelinde daha kapsamlı bir hata loglama ve kullanıcı bilgilendirme sisteminin kurulması.

Not:
Bu proje bir Software Engineering öğrencisi tarafından CBS ve 3D simülasyon yeteneklerini test etmek amacıyla geliştirilmiştir.
