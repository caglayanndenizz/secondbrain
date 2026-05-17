# 🪄 VFX & UI Geliştirme Notları

## 🎨 Efektler (VFX)

> [!TIP] 16x16 vs 32x32 Çözünürlük Dengesi
> Projede iki farklı çözünürlüğü karıştırmak **sorun yaratmaz**. Tek şart, **Pixels Per Unit (PPU)** değerini orantılı tutmaktır.
> - **16x16 Sprite** $\rightarrow$ `PPU = 16`
> - **32x32 Sprite** $\rightarrow$ `PPU = 32`
> 
> *Bu sayede her iki sprite da Unity dünyasında aynı boyutta görünür ve piksel estetiği bozulmaz.*

### ⚔️ Efekt Kategorileri ve Yaklaşımlar

| Efekt Türü                | Uygulanacak Yöntem / Yaklaşım                                     |
| :------------------------ | :---------------------------------------------------------------- |
| 🔥 **Fire Arrow Hit**     | Looping ateş particle + Sprite Flash *(renk kodu zaten var)*      |
| 🧪 **Poison Arrow Hit**   | Yeşil puf particle burst + Zamana yayılan yavaş renk pulse efekti |
| ⚡ **AoE Blast (Charged)** | Shockwave ring sprite animasyonu + Radial particle burst          |
| ❄️ **Freeze**             | Mavi ice shard particle veya düşman üzerine overlay sprite        |

### 🛠️ Entegrasyon Yöntemleri

* **Unity Particle System (Built-in):** En hızlı ve performanslı yol. Piksel sanat çizgisini korumak için şu ayarlara dikkat et:
	* `Renderer > Sorting Layer` ayarını doğru katmana ver.
	* `Material` olarak **Sprites-Default** kullan.
* **Asset Store Seçeneği:** *"Pixel Particle Effects"* aramasıyla 16x16/32x32 sprite sheet içeren hazır paketleri toplayıp projeye bir günde entegre edebilirsin.

---

## 🖥️ UI — Eksik Listesi

> [!ATTENTION] Kodda Var Ama Görseli/Prefab'ı Eksik Olanlar
> Aşağıdaki sistemlerin script mimarisi hazır, sadece sahne içi yerleştirme veya asset bağlamaları yapılacak.

- [ ] **Cevher Sistemi** (`CevherSystemUI.cs`) $\rightarrow$ Sahnede prefab oluşturulacak ve Inspector bağlantıları yapılacak.
- [ ] **Augment Seçim Ekranı** (`AugmentSelectionUI.cs`) $\rightarrow$ Görsel tasarım ve panel yerleşimi eksik.
- [ ] **Oyuncu Can Barları** (`PlayerBarsUI.cs`) $\rightarrow$ Can ve enerji barlarının görsel asset'leri bağlanacak.
- [ ] **Ok Statü Göstergesi** $\rightarrow$ Hangi okun (örn. Fire Arrow) aktif olduğunu gösteren dinamik bir ikon eksik.
- [ ] **Augment Slot Göstergesi** $\rightarrow$ Kaç slotun dolu, kaçının boş olduğunu gösteren UI indikatörü.

---

## 📈 Yol Haritası & Öncelik Sıralaması

> [!TODO] Geliştirme Sırası

1. **Cevher UI Bağlantısı**
	- *Neden:* Kod zaten hazır, sadece sahne işi olduğu için en hızlı ayağa kalkacak iş.
2. **Ok Statü İkonları**
	- *Neden:* Yapımı basit ama oynanış hissiyatına (feedback) etkisi çok yüksek.
3. **VFX & Particle Efektleri**
	- *Neden:* En çok zamanı alacak kısım ama oyunun vuruş hissini (juice) doğrudan belirleyecek.
4. **Augment Slot Göstergesi**
	- *Neden:* "Nice-to-have" (olsa güzel olur) aşaması, cila aşamasında eklenebilir.