# Ai-Movie-Stream-Go-App

AI destekli film akış platformu için Go ile geliştirilmiş RESTful API backend servisi.

## 📋 Proje Hakkında

MagicStreamMovies, film verilerini yönetmek ve sunmak için tasarlanmış bir backend API servisidir. MongoDB veritabanı kullanarak film bilgilerini saklar ve Gin framework ile hızlı ve güvenilir bir REST API sunar.

## 🏗️ Mimari

Proje, temiz kod prensiplerine uygun olarak modüler bir yapıda tasarlanmıştır:

```
Server/MagicStreamMoviesServer/
├── controllers/     # HTTP isteklerini yöneten controller'lar
├── models/          # Veri modelleri (Movie, Genre, Ranking)
├── database/        # MongoDB bağlantı yönetimi
├── routes/          # API route tanımlamaları
├── middleware/      # Middleware fonksiyonları
├── utils/           # Yardımcı fonksiyonlar
└── main.go          # Uygulama giriş noktası
```

## 🚀 Özellikler

- ✅ RESTful API tasarımı
- ✅ MongoDB veritabanı entegrasyonu
- ✅ Film listesi getirme (GetMovies)
- ✅ IMDB ID ile tek film getirme (GetMovie)
- ✅ Film modeli: IMDB ID, başlık, poster, YouTube video, tür, admin incelemesi, sıralama
- ✅ Environment variable desteği (.env)
- ✅ Context timeout yönetimi

## 📦 Teknolojiler

- **Go 1.25.1** - Programlama dili
- **Gin** - Web framework
- **MongoDB Driver v2** - Veritabanı driver'ı
- **godotenv** - Environment variable yönetimi

## 🔧 Kurulum

### Gereksinimler

- Go 1.25.1 veya üzeri
- MongoDB (yerel veya cloud)
- Git

### Adımlar

1. Projeyi klonlayın:

```bash
git clone https://github.com/yldzEmreOmer/Ai-Movie-Stream-Go-App.git
cd Ai-Movie-Stream-Go-App
```

2. Server dizinine gidin:

```bash
cd Server/MagicStreamMoviesServer
```

3. Bağımlılıkları yükleyin:

```bash
go mod download
```

4. `.env` dosyası oluşturun:

```env
MONGODB_URI=mongodb://localhost:27017
DATABASE_NAME=magicstreammovies
```

5. Sunucuyu başlatın:

```bash
go run main.go
```

Sunucu `http://localhost:8080` adresinde çalışacaktır.

## 📡 API Endpoints

### GET `/hello`

Test endpoint'i - "Hello, World!" mesajı döner.

**Response:**

```
Hello, World!
```

### GET `/movies`

Tüm filmleri listeler.

**Response:**

```json
[
  {
    "id": "...",
    "imdb_id": "tt1234567",
    "title": "Film Adı",
    "poster_path": "https://...",
    "youtube_id": "abc123",
    "genre": [
      {
        "genre_id": 1,
        "genre_name": "Aksiyon"
      }
    ],
    "admin_review": "Film hakkında inceleme...",
    "ranking": {
      "ranking_value": 8,
      "ranking_name": "Mükemmel"
    }
  }
]
```

### GET `/movies/:imdb_id`

IMDB ID'ye göre tek bir film getirir.

**Parameters:**

- `imdb_id` (path parameter) - Film'in IMDB ID'si

**Response:**

```json
{
  "id": "...",
  "imdb_id": "tt1234567",
  "title": "Film Adı",
  "poster_path": "https://...",
  "youtube_id": "abc123",
  "genre": [...],
  "admin_review": "...",
  "ranking": {...}
}
```

## 📊 Veri Modeli

### Movie

```go
type Movie struct {
    ID          bson.ObjectID
    ImdbID      string
    Title       string
    PosterPath  string
    YoutubeID   string
    Genre       []Genre
    AdminReview string
    Ranking     Ranking
}
```

### Genre

```go
type Genre struct {
    GenreID   int
    GenreName string
}
```

### Ranking

```go
type Ranking struct {
    RankingValue int
    RankingName  string
}
```

## 🔐 Environment Variables

Proje çalışması için aşağıdaki environment variable'lar gereklidir:

- `MONGODB_URI` - MongoDB bağlantı string'i
- `DATABASE_NAME` - Kullanılacak veritabanı adı

## 📝 Geliştirme

Proje üzerinde çalışırken:

1. Yeni endpoint eklemek için `controllers/` klasörüne yeni controller ekleyin
2. Yeni model eklemek için `models/` klasörünü kullanın
3. Route tanımlamaları için `routes/` klasörünü kullanın
4. Middleware'ler için `middleware/` klasörünü kullanın

## 🤝 Katkıda Bulunma

1. Fork edin
2. Feature branch oluşturun (`git checkout -b feature/amazing-feature`)
3. Commit edin (`git commit -m 'Add some amazing feature'`)
4. Push edin (`git push origin feature/amazing-feature`)
5. Pull Request açın

## 📄 Lisans

Bu proje açık kaynaklıdır.

## 👤 Yazar

**yldzEmreOmer**

- GitHub: [@yldzEmreOmer](https://github.com/yldzEmreOmer)

---
