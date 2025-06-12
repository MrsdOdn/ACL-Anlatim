# ACL-Anlatim
Ağ ve güvenlik konularına yeni başlayanlar için Erişim Kontrol Listeleri (ACL) kavramını anlaşılır kılan bir rehber.


## 🧠 Subnet Maskesi ve Wildcard Maskesi (ACL Bağlantılı Açıklama)

ACL (Access Control List) konusuna girmeden önce, IP adresi filtreleme işlemlerinde kullanılan **Subnet Maskesi** ve **Wildcard Maskesi** kavramlarını kavramak önemlidir.

### 🏫 Sınıf Benzetmesiyle Anlatım:

**IP Alt Ağı (Sınıf)**  
`192.168.1.0/24` = 256 kişilik bir sınıf (IP adresleri)

---

### 🧩 Subnet Maskesi → “Ağ mı, cihaz mı?” sorusunun cevabı

**Subnet maskesi**, IP adresini ikiye ayırır:

- 📘 **Ağ kısmı** → Herkesin ortak okul numarası gibi (örnek: `192.168.1`)
- 👤 **Cihaz (Host) kısmı** → Kişisel sıra numarası gibi (örnek: `.15`, `.25`)

> Örnek: `255.255.255.0` → İlk 3 oktet "ağ", son oktet "cihaz" anlamına gelir.

Bu ayrım **kesindir**: Ya ağdasın, ya hostsın. Gri alan yoktur.

---

### 🎯 Wildcard Maskesi → “Kimleri seçeceğim?” sorusunun cevabı

**Wildcard maskesi**, daha esnek seçimler yapmana olanak tanır.  
Subnet maskesindeki gibi "keskin ayrım" yerine, IP adresinin hangi bitlerinin **önemli** olduğunu belirtir:

- `0` → Bu bit **eşleşmeli**
- `1` → Bu bit **önemsiz** (fark etmez)

🧠 Düşün: "Sınıfta sadece sporcu kızları seç" gibi özel filtreler yapmak istiyorsan, wildcard maskesi gerekir.

#### Örnekler:

- `0.0.0.255` → Son okteti fark etmez → `192.168.1.x` tüm IP'leri seçilir  
- `0.0.0.1` → Sadece son bit fark etmez → Çift/tek IP seçimi yapılabilir  
- `0.0.255.0` → 3. oktet serbest → `192.168.x.0` gibi daha geniş filtreler

---

### 🔐 ACL’lerde Neden Wildcard Kullanılır?

ACL (Access Control List) gibi IP filtreleme sistemlerinde **subnet maskesi değil**, **wildcard maskesi** kullanılır.  
Çünkü:

✅ Daha esnek  
✅ Daha detaylı filtreleme yapılabilir  
✅ Belirli IP desenlerine göre kurallar tanımlanabilir

---

### 📦 Özet Karşılaştırma Tablosu

| Özellik              | Subnet Maskesi               | Wildcard Maskesi               |
|----------------------|------------------------------|-------------------------------|
| Yapı                 | `1` → ağ, `0` → host         | `0` → eşleşmeli, `1` → fark etmez |
| Kullanım Alanı       | Ağ adresleme, subnetting     | ACL, IP filtreleme             |
| Esneklik             | Sabit                        | Esnek                          |
| ACL’de Kullanımı     | ❌ Kullanılmaz               | ✅ Aktif olarak kullanılır     |

---

### 🎯 Sonuç

Wildcard maskesi, ACL kurallarında esnek ve hedef odaklı IP filtrelemeleri yapmanı sağlar.  
Subnet maskesi sadece "ağ nerede başlar, nerede biter?" sorusuna cevap verirken;  
Wildcard maskesi, "ağın içindeki **hangi IP’ler** önemli?" sorusuna odaklanır.

Bu farkı anlamak, doğru ve güvenli ağ erişim kontrolü kurallarını yazabilmenin temelidir.
