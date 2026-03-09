# MERN Stack Task Management & Architecture App

Bu proje, Katmanlı Mimari (Layered Architecture) prensiplerine sadık kalarak geliştirilmiş, tam donanımlı bir MERN (MongoDB, Express, React, Node.js) yığını uygulamasıdır. Proje, kimlik doğrulama, Kanban tarzı görev yönetimi ve özel geliştirilmiş bir mimari şema görselleştirmesi içerir.

## 🚀 Proje Özellikleri

*   **Katmanlı Mimari (Backend)**: Router -> Controller -> Service -> Repository katman ayırımı sayesinde temiz ve bakımı kolay kod tabanı.
*   **Kanban Board Görev Yönetimi**: "Yapılacak", "Devam Ediyor" ve "Tamamlandı" sütunları ile dinamik görev takibi.
*   **Gerçek Zamanlı İstatistikler**: Toplam görev, tamamlanan, geciken ve bugün biten görevlerin anlık analizi.
*   **Kullanıcı Kimlik Doğrulama**: JWT (JSON Web Tokens) ve bcrypt ile güvenli şifreleme ve kullanıcı oturum yönetimi.
*   **Modern Arayüz (Frontend)**: React, Vite, ve Tailwind CSS v4 kullanılarak tasarlanmış "Glassmorphism" odaklı karanlık tema (Dark Mode).
*   **Tamamen Duyarlı (Responsive)**: Mobil, tablet ve masaüstü cihazlarla tam uyumlu arayüz.
*   **Mimari Şema Sayfası (`/architecture`)**: Projenin arka uç veri akışını gösteren özel görselleştirme ekranı.

## 🛠 Kullanılan Teknolojiler

### Backend
*   **Node.js & Express.js**: RESTful API sunucusu.
*   **MongoDB & Mongoose**: NoSQL veritabanı ve ODM (Object Data Modeling).
*   **JSON Web Token (JWT)**: Rota koruması ve kimlik doğrulama.
*   **Bcrypt.js**: Kullanıcı şifrelerinin hash'lenmesi.
*   **Express Rate Limit & Helmet**: Temel API güvenlik önlemleri.
*   **Express Validator**: Gelen İstek (Request) gövde verilerinin doğrulanması.

### Frontend
*   **React (Vite ile)**: Hızlı ve modern kullanıcı arayüzü kütüphanesi.
*   **Tailwind CSS v4**: Utility-first stil çerçevesi (CSS değişkenleri ile yapılandırılmıştır).
*   **React Router DOM**: İstemci tarafı sayfa yönlendirmeleri.
*   **Axios**: Backend API'sine HTTP istekleri yapmak için yapılandırılmış HTTP istemcisi.
*   **Lucide React**: Modern ve pürüzsüz SVG ikonlar.
*   **Date-fns**: Görev teslim tarihlerinin ve istatistiklerin hesaplanması.

## 📁 Katmanlı Proje Yapısı

\`\`\`
web 2/
├── backend/                  # Node.js + Express API Sunucusu
│   ├── src/
│   │   ├── config/           # Veritabanı (db.js) ayarları
│   │   ├── controllers/      # HTTP İstek/Yanıt yönetim katmanı
│   │   ├── middleware/       # JWT Protect (Auth) ve Hata Yönetimi
│   │   ├── models/           # Mongoose Veritabanı Şemaları (User, Task)
│   │   ├── repositories/     # Veritabanı İletişim(CRUD) Katmanı
│   │   ├── routes/           # API Uç Noktaları (Routes)
│   │   ├── services/         # İş Mantığı (Business Logic) Katmanı
│   │   ├── utils/            # JWT Token vb. yardımcı fonksiyonlar
│   │   ├── validators/       # Express-validator kuralları
│   │   └── app.js            # Express app konfigürasyonu
│   ├── .env                  # Çevresel değişkenler
│   └── server.js             # Sunucu başlatıcı (Entry point)
│
└── frontend/                 # React + Vite Vite İstemcisi
    ├── src/
    │   ├── components/       # Yeniden kullanılabilir UI bileşenleri (TaskCard, vb.)
    │   ├── context/          # React Context API (AuthContext)
    │   ├── pages/            # Ana Sayfa Bileşenleri (Login, Tasks, Architecture)
    │   ├── utils/            # Axios API istemcisi
    │   ├── App.jsx           # Ana Router tanımı
    │   └── index.css         # Tailwind v4 direktifleri (@theme) ve Global CSS
    └── package.json
\`\`\`

## ⚙️ Kurulum ve Çalıştırma

### Gereksinimler
*   [Node.js](https://nodejs.org/) (v16 veya üzeri)
*   [MongoDB](https://www.mongodb.com/) (Yerel sunucu veya MongoDB Atlas)

### Adım 1: Depoyu Klonlayın

Terminali açın ve projeyi ana bilgisayarınıza indirin (Eğer bir Git deposuysa):

\`\`\`bash
git clone <proje-url>
cd "web 2"
\`\`\`

### Adım 2: Çevresel Değişkenleri Ayarlayın (.env)
`backend/` klasörü içinde bir `.env` dosyası oluşturun ve aşağıdaki değerleri ekleyin:
\`\`\`env
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://localhost:27017/mern-architecture
JWT_SECRET=super_secret_jwt_key_degistirmelisiniz_12345
JWT_EXPIRE=30d
\`\`\`

*(Not: `MONGODB_URI` değerini kullanacağınız yerel MongoDB kurulumuna veya Atlas bağlantısına göre ayarlayın.)*

### Adım 3: Backend Sunucusunu Çalıştırın
Yeni bir terminalde:
\`\`\`bash
cd backend
npm install
npm run dev
\`\`\`
*Sunucu `http://localhost:5000` adresinde başlayacaktır.*

### Adım 4: Frontend Sunucusunu Çalıştırın
Farklı ve yeni bir terminalde:
\`\`\`bash
cd frontend
npm install
npm run dev
\`\`\`
*İstemci `http://localhost:5173` (veya 5174/5175 vb.) adresinde başlayacaktır.*

## 📸 Ekran Görüntüleri ve İşleyiş

*   **Giriş ve Kayıt Sayfaları**: Minimalist Glassmorphism (Cam Efekti) ile tasarlanmıştır.
*   **Kanban Dashboard (Panom)**: Sol sütunda toplam istatistikler, ortada görev filtreleri ve tam ekran `Yapılacak`, `Devam Ediyor` ve `Tamamlandı` sütunlarından oluşan sürüklenebilir tarzda UI paneli yer alır.
*   **Mimari Şema**: Üst gezinti (nav) çubuğundaki **Mimari** sekmesine tıklanarak, Controller -> Service -> Repository bilgi akış şeması incelenebilir.

---
*Geliştirme: Antigravity Code Assistant yardımıyla inşa edilmiştir.*
