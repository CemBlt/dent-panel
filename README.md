# Dişçi Bul - Yönetim Paneli (Django)

Bu depo, Dişçi Bul uygulamasının Django tabanlı yönetim panelini içermektedir. Panel, hastaneler, doktorlar, randevular ve kullanıcı yönetimi gibi tüm backend operasyonlarını yönetmek için kullanılmaktadır.

## Mimari Genel Bakış

- **Dil:** Python 3.9+
- **Framework:** Django 5.2+
- **Backend Entegrasyonu:** Supabase (PostgreSQL veritabanı ve Storage)
- **Servis Katmanı:** Supabase ile etkileşimi soyutlayan servisler (`hospital_service`, `appointment_service`, `doctor_service` vb.)
- **Kimlik Doğrulama:** Django'nun kendi kimlik doğrulama sistemi ve Supabase Auth entegrasyonu
- **E-posta:** Gmail SMTP üzerinden e-posta gönderimi

## Özellikler

- 🏥 **Hastane Yönetimi:** Hastane kayıt, düzenleme, çalışma saatleri ve tatil günleri yönetimi
- 👨‍⚕️ **Doktor Yönetimi:** Doktor ekleme, düzenleme, servis atama
- 📅 **Randevu Yönetimi:** Randevu görüntüleme, filtreleme, iptal etme
- ⭐ **Değerlendirme Yönetimi:** Kullanıcı yorumları ve puanlamalarını görüntüleme ve yönetme
- 👤 **Kullanıcı Yönetimi:** Kullanıcı profillerini görüntüleme ve yönetme
- 📊 **Dashboard:** Sistem istatistikleri ve özet bilgiler
- 📧 **E-posta Bildirimleri:** Randevu onayları ve hatırlatmaları

## Kurulum ve Çalıştırma

### 1. Ön Gereksinimler

- Python 3.9 veya üzeri
- `pip` (Python paket yöneticisi)
- Git
- Bir Supabase projesi (URL ve API anahtarları gereklidir)
- Gmail hesabı (e-posta gönderimi için)

### 2. Depoyu Klonlama

```bash
git clone https://github.com/CemBlt/dent-panel.git
cd dent-panel
```

### 3. Sanal Ortam Oluşturma

```bash
python -m venv venv
```

**Windows:**
```bash
venv\Scripts\activate
```

**Linux/macOS:**
```bash
source venv/bin/activate
```

### 4. Bağımlılıkları Yükleme

```bash
pip install -r requirements.txt
```

### 5. Ortam Değişkenlerini Yapılandırma

`.env` dosyasını `dent-panel` dizininde oluşturun ve `ENV_SETUP_GUIDE.md` dosyasındaki talimatlara göre Supabase ve e-posta ayarlarınızı yapılandırın.

**Örnek `.env` dosyası:**
```env
# Supabase Ayarları
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
SUPABASE_ANON_KEY=your-anon-key

# Email Ayarları
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password
DEFAULT_FROM_EMAIL=your-email@gmail.com
ADMIN_EMAIL=admin@example.com

# Django Ayarları
DJANGO_SECRET_KEY=your-secret-key-here
```

Detaylı kurulum talimatları için `ENV_SETUP_GUIDE.md` dosyasına bakın.

### 6. Veritabanı Migrasyonları

```bash
python manage.py migrate
```

### 7. Süper Kullanıcı Oluşturma

```bash
python manage.py createsuperuser
```

### 8. Sunucuyu Başlatma

```bash
python manage.py runserver
```

Panel artık `http://127.0.0.1:8000/panel/` adresinde çalışıyor olmalı.

## Testler

Proje, Django servislerini test etmek için unit testler içermektedir:

```bash
python manage.py test panel
```

Testler Supabase çağrılarını mock'layarak çalışır, bu nedenle gerçek bir Supabase bağlantısı gerektirmez.

## Proje Yapısı

```
dent-panel/
├── dent_admin_panel/      # Django proje ayarları
├── panel/                 # Ana uygulama
│   ├── services/          # Supabase servisleri
│   ├── views/            # View fonksiyonları
│   ├── templates/        # HTML şablonları
│   ├── static/           # CSS ve JavaScript dosyaları
│   └── tests/            # Unit testler
├── manage.py
├── requirements.txt
├── ENV_SETUP_GUIDE.md    # Detaylı kurulum rehberi
└── README.md
```

## Servisler

Panel, Supabase ile etkileşim için aşağıdaki servisleri içerir:

- `hospital_service.py` - Hastane yönetimi
- `doctor_service.py` - Doktor yönetimi
- `appointment_service.py` - Randevu yönetimi
- `review_service.py` - Değerlendirme yönetimi
- `user_service.py` - Kullanıcı yönetimi
- `email_service.py` - E-posta gönderimi
- `event_service.py` - Telemetri event loglama

## CI/CD

Proje, her `push` ve `pull_request` olayında otomatik olarak testleri çalıştıran bir GitHub Actions workflow'una sahiptir. Workflow, `/.github/workflows/ci.yml` dosyasında tanımlanmıştır.

## Katkıda Bulunma

Katkılarınız memnuniyetle karşılanır! Lütfen bir özellik eklemeden veya hata düzeltmeden önce mevcut kod stilini ve mimari prensiplerini inceleyin. Herhangi bir değişiklik için bir `pull request` açmadan önce ilgili testleri yazmayı ve CI'ın yeşil geçtiğinden emin olmayı unutmayın.

## İlgili Projeler

- **Mobil Uygulama:** [dent-mobile](https://github.com/CemBlt/dent-mobile) - Flutter tabanlı mobil uygulama

## Lisans

Bu proje özel bir projedir.

