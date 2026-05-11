# azuredb
# AzureCloud ☁️

**AzureCloud** — Windows masaüstü için geliştirilmiş, çok amaçlı bir cloud dosya yöneticisi, kod editörü, SSH/VDS remote bağlantı aracı ve şifreli arşiv yöneticisidir.

![Version](https://img.shields.io/badge/sürüm-0.1.1-blue)
![.NET](https://img.shields.io/badge/.NET-8.0-purple)
![Platform](https://img.shields.io/badge/platform-Windows-green)
![License](https://img.shields.io/badge/license-MIT-orange)

---

## Özellikler

### 📁 Cloud Dosya Yöneticisi
- Yerel klasör tabanlı cloud dosya yönetimi
- Dosya yükleme, indirme, silme, yeniden adlandırma
- Klasör içi gezinme (Geri/İleri butonları ile)
- Çift tıklama ile dosya açma (kod dosyaları editörde, diğerleri varsayılan programda)
- Dosya özellikleri görüntüleme (boyut, tarih, öznitelik)

### ✍️ Kod Editörü
- Sözdizimi vurgulama: C#, Python, JavaScript, HTML, CSS, SQL, JSON
- Otomatik dil algılama (dosya uzantısına göre)
- Manuel dil seçimi
- Satır numaraları
- Bul/Değiştir (Ctrl+F / Ctrl+H)
- Satıra Git (Ctrl+G)
- Kod çalıştırma (F5): Python, Node.js, C# Script, HTML, BAT, PowerShell, Ruby, Go, Java, PHP, Perl
- Performans için WM_SETREDRAW ile optimize edilmiş vurgulama

### 🔐 .peacy Arşiv Yöneticisi
- AES-256-CBC şifreleme ile özel arşiv formatı
- PBKDF2 anahtar türetme (100.000 iterasyon)
- Arşiv oluşturma, açma, listeleme, dosya ekleme, çıkartma
- Şifreli ve şifresiz arşiv desteği
- SHA-256 dosya bütünlük doğrulama

### 🌐 VDS Remote Bağlantı (SSH)
- SSH.NET kütüphanesi ile güvenli shell bağlantısı
- Gerçek zamanlı terminal çıktısı
- Kayıtlı bağlantı yönetimi
- Komut gönderme

### ⚙️ Kurulum Sihirbazı
- İlk çalıştırmada otomatik açılan 5 adımlı kurulum
- Dil seçimi (Türkçe / English)
- Lisans sözleşmesi onayı
- Cloud klasörü seçimi
- Bileşen seçimi
- Splash açılış ekranı

---

## Ekran Görüntüleri

| Ana Ekran | Kod Editörü | VDS Remote |
|-----------|-------------|------------|
| Dosya yöneticisi | Sözdizimi vurgulamalı editör | SSH terminal |
| Kurulum Sihirbazı | .peacy Arşiv | Hakkında |
| 5 adımlı kurulum | Şifreli arşiv yönetimi | Versiyon bilgisi |

---

## Sistem Gereksinimleri

- **İşletim Sistemi:** Windows 10 / 11 (64-bit)
- **Runtime:** .NET 8.0 (self-contained publish ile dahil)
- **Depolama:** ~170 MB (self-contained)
- **İnternet:** VDS bağlantısı için gerekli

---

## Kurulum

### Hazır Binary
1. [Son sürümü indir](https://github.com/AzureCloudApp/AzureCloud/releases)
2. `AzureCloud.exe` dosyasını çalıştırın
3. Kurulum sihirbazını takip edin

### Kaynak Koddan Derleme
```bash
git clone https://github.com/AzureCloudApp/AzureCloud.git
cd AzureCloud
dotnet restore
dotnet build -c Release
dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true
```

---

## Kullanım

### İlk Çalıştırma
1. Uygulamayı açın → Kurulum sihirbazı otomatik başlar
2. Dil seçin → Lisansı kabul edin → Cloud klasörünü belirleyin
3. Bileşenleri seçin → Kurulumu tamamlayın

### Dosya Yönetimi
- Dosyaları cloud klasörüne sürükleyin veya "Yükle" butonunu kullanın
- Klasörlere çift tıklayarak girin, Geri/İleri ile gezinin
- Kod dosyaları (.cs, .js, .py, .html vb.) editörde açılır

### Kod Editörü
- F5 ile kodu çalıştırın (dil desteğine göre)
- Ctrl+F ile arama, Ctrl+H ile değiştirme
- Sağ alttan dil seçin

### SSH Bağlantısı
- Araçlar → VDS Remote Bağlantı
- Host, port, kullanıcı adı ve şifre girin
- Bağlan butonuna tıklayın

### Arşiv Yönetimi
- Araçlar → .peacy Arşiv Yöneticisi
- Yeni arşiv oluşturun veya mevcut .peacy dosyasını açın
- Şifreli arşivleme için güçlü bir şifre belirleyin

---

## Teknolojiler

| Teknoloji | Kullanım |
|-----------|----------|
| C# / .NET 8 | Uygulama çatısı |
| Windows Forms | Kullanıcı arayüzü |
| SSH.NET | SSH bağlantısı |
| AES-256-CBC | Dosya şifreleme |
| PBKDF2 | Anahtar türetme |
| JSON | Ayarlar ve manifest |
| System.IO.Compression | ZIP arşivleme |
| P/Invoke (WM_SETREDRAW) | RichTextBox performansı |

---

## Proje Yapısı

```
AzureCloud/
├── Program.cs                  # Giriş noktası, hata yönetimi
├── Form1.cs                    # Ana dosya yöneticisi
├── CloudApp.csproj             # Proje dosyası
│
├── Forms/
│   ├── SplashForm.cs           # Açılış ekranı
│   ├── SetupWizard.cs          # Kurulum sihirbazı
│   ├── EditorForm.cs           # Kod editörü
│   ├── ArchiveForm.cs          # .peacy arşiv yöneticisi
│   ├── VdsForm.cs              # SSH/VDS remote
│   └── AboutForm.cs            # Hakkında penceresi
│
├── Helpers/
│   ├── CryptoHelper.cs         # AES-256 şifreleme
│   └── PeacyArchive.cs         # .peacy arşiv formatı
│
└── Resources/
    ├── AppSettings.cs           # Uygulama ayarları
    ├── SettingsHelper.cs        # VDS bağlantı ayarları
    └── Resources.cs             # Logo görseli
```

---

## Lisans

Bu proje **MIT Lisansı** ile lisanslanmıştır. Detaylar için `LICENSE` dosyasına bakın.

---

## İletişim

- GitHub: [github.com/AzureCloudApp](https://github.com/AzureCloudApp)
- Sürüm: **0.1.1**
- Geliştirme: Aktif

---

*AzureCloud - C# Windows Forms ile geliştirilmiştir.*

