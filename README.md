# Laravel API Projesi

Bu proje, Laravel framework'ü kullanılarak geliştirilmiş basit bir API uygulamasıdır. Kullanıcı kaydı, girişi ve profil bilgilerini görüntüleme gibi temel özellikleri içerir.

## Özellikler

- 🔐 Kullanıcı Kimlik Doğrulama (Laravel Sanctum)
  - Kayıt olma
  - Giriş yapma
  - Kullanıcı bilgilerini görüntüleme
  - Çıkış yapma
- 🛡️ Güvenlik Önlemleri
  - Token tabanlı kimlik doğrulama
  - API Rate Limiting (dakikada 10 istek)
  - Form validation
  - Password hashing

## Gereksinimler

- PHP >= 8.1
- Composer
- MySQL/PostgreSQL
- Laravel 10.x

## Kurulum

1. Projeyi klonlayın:
```bash
git clone https://github.com/your-username/laravel-api-project.git
cd laravel-api-project
```

2. Bağımlılıkları yükleyin:
```bash
composer install
```

3. `.env` dosyasını oluşturun:
```bash
cp .env.example .env
```

4. `.env` dosyasını düzenleyin ve veritabanı bilgilerinizi girin:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel_api
DB_USERNAME=root
DB_PASSWORD=
```

5. Uygulama anahtarını oluşturun:
```bash
php artisan key:generate
```

6. Veritabanı tablolarını oluşturun:
```bash
php artisan migrate
```

7. Sanctum kurulumunu tamamlayın:
```bash
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```

## API Endpointleri

### Kimlik Doğrulama Endpointleri

| Metod | Endpoint | Açıklama |
|-------|----------|-----------|
| POST | `/api/register` | Yeni kullanıcı kaydı |
| POST | `/api/login` | Kullanıcı girişi |
| GET | `/api/user` | Kullanıcı bilgilerini görüntüleme |
| POST | `/api/logout` | Çıkış yapma |

## Örnek İstekler

### Kayıt Olma
```http
POST /api/register
Content-Type: application/json

{
    "name": "Test User",
    "email": "test@example.com",
    "password": "password123",
    "password_confirmation": "password123"
}
```

### Giriş Yapma
```http
POST /api/login
Content-Type: application/json

{
    "email": "test@example.com",
    "password": "password123"
}
```

### Kullanıcı Bilgilerini Görüntüleme
```http
GET /api/user
Authorization: Bearer {your_token}
```

## Güvenlik Önlemleri

1. **Rate Limiting**: Her kullanıcı için dakikada maksimum 10 istek sınırı bulunmaktadır.
2. **Token Authentication**: Tüm istekler için geçerli bir Bearer token gereklidir.
3. **Validation**: Tüm gelen veriler sıkı bir şekilde doğrulanır.
4. **Password Hashing**: Kullanıcı şifreleri güvenli bir şekilde hashlanarak saklanır.

## Test

Projeyi test etmek için:

```bash
php artisan test
```

## Postman Koleksiyonu

API'yi test etmek için Postman koleksiyonunu kullanabilirsiniz. Koleksiyon dosyası `postman/api-collection.json` dizininde bulunmaktadır.

## Lisans

Bu proje MIT lisansı altında lisanslanmıştır. Daha fazla bilgi için [LICENSE](LICENSE) dosyasına bakınız.

## İletişim

Sorularınız için:
- Email: your-email@example.com
- GitHub: [your-username](https://github.com/your-username)
