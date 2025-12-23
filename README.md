## Kategori Öneri Algoritması – Akış Diyagramı

```mermaid
flowchart TD
  A([Uygulama Başlar / Fonksiyon Çağrılır]) --> B[Inputları al: userProfile, allCategories, context, limit]
  B --> C[Verileri normalize et: küçük harf, trim, eşleştirme mapleri]
  C --> D{Alerjen var mı?}
  D -- Evet --> E[Hard Block: Alerjenle ilişkili kategorileri tamamen çıkar]
  D -- Hayır --> F[Hard Block yok]
  E --> G[Skor tablosu oluştur: categoryScores = 0]
  F --> G

  G --> H[User seviyesini hesapla: cold / mature]
  H --> I[Weight'leri belirle]
  I --> J[Profil kategorilerine puan ekle]
  J --> K[Soft Block: Diyete uymayanlara ceza]
  K --> L[Diyete uygunlara bonus]
  L --> M[Favorilerden puan ekle]
  M --> N[Son görüntülenenlerden recency puanı]
  N --> O[Bağlam ekle: saat/mevsim]

  O --> P[Hard-block edilenleri çıkar]
  P --> Q[Skora göre sırala]
  Q --> R{Pozitif skor var mı?}
  R -- Evet --> S[Pozitiflerden limit kadar seç]
  R -- Hayır --> T[En üstten limit kadar seç]

  S --> U{Limit doldu mu?}
  T --> U
  U -- Hayır --> V[Fallback ile doldur]
  U -- Evet --> W[Sonuç hazır]

  V --> W
  W --> X([Return: topCategories])
