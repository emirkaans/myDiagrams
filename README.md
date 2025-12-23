flowchart LR
  A([Fonksiyon Başlar]) --> B[Inputları Al & Normalize Et]
  B --> C{Alerjen Kontrolü}
  C -- Var --> D[Hard Block: Uyuşmayanları Çıkar]
  C -- Yok --> E[Devam Et]

  D --> F[Skor Tablosu Oluştur]
  E --> F

  F --> G[Kullanıcı Seviyesi Belirle<br/>(Cold / Mature)]
  G --> H[Ağırlıkları Ayarla]

  H --> I[Profil & Diyet Etkisi]
  I --> J[Favori & Geçmiş Etkileşimler]
  J --> K[Zamansal / Bağlamsal Bonus]

  K --> L[Filtrele & Sırala]
  L --> M{Pozitif Skor Var mı?}
  M -- Evet --> N[En İyi Kategorileri Seç]
  M -- Hayır --> O[Varsayılan Kategoriler]

  N --> P([Sonuç])
  O --> P
