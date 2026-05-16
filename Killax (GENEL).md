# 🎮 Game Feel & Roguelike Geliştirme Notları

## ⚡ Oyun Hissi (Game Feel) — En Hızlı Etki

> [!TIP] Küçük Dokunuşlar, Büyük Hissiyat
> - **Hit Stop:** Ok veya hammer düşmana değdiğinde oyunu 1-2 frame dondurma (`Time.timeScale = 0.05f` → Coroutine ile eski haline getir). Çok basit bir kodlama ile dövüş mekaniğini inanılmaz dramatik hale getirir.
> - **Ses Eksikliği:** Şu an kod mimarisinde ses (Audio) referansı bulunmuyor. Yay çekme, ok isabeti, Hammer Slam, Dash veya augment alma gibi temel eylemlere ses eklemek oyunun boşluk hissini yok eder. *Freesound.org* veya *Kenney* asset'leri ile 1 günde çözülebilir.

---

## 🌀 Roguelike Derinliği

* **Meta Progression (Kalıcı İlerleme) Eksik:** Her run tamamen aynı başlangıçla açılıyor. Oyunun tekrar oynanabilirliğini (*retention*) artırmak için *"Unlockable (açılabilir) başlangıç augmenti"* veya *"kalıcı pasif bonuslar"* eklenmeli.
* **Cevher Sistemi Ara Ödülleri Zayıf:** Mevcut yapıda 2 → Altın, 4 → Elmas, 6 → Obsidyen basamakları var ancak sadece Obsidyen gerçek bir fark yaratıyor.
  * *Çözüm:* 2 cevherde küçük pasif (+%5 ok hızı), 4 cevherde orta pasif (+1 ok) gibi her eşiği (*threshold*) anlamlı kılacak ödüller verilmeli.
* **Shop / Event Odaları Yok:** Dungeon Generator mimarisine özel oda tipleri (Define Room) entegre edilebilir mi? *Rest Room, Merchant (Tüccar) veya Challenge Odaları* derinlik katar.

---

## ⚠️ Oyunun Zayıf Noktaları

> [!ATTENTION] Kritik Eksikler
> * **Augment Açıklamaları (Tooltip):** `AugmentSelectionUI` var fakat oyuncu *"FireArrowUnlock"* kartının tam olarak ne işe yaradığını göremiyorsa seçim yapamaz. Net bir Tooltip / Description sistemi şart.
> * **Düşman Çeşitliliği:** Mekaniksel olarak Freeze, Fire ve Poison DoT (Zamanla hasar) eklendi ancak bunları exploit eden veya bunlara direnç gösteren düşman tipleri yok. Bu durum sistemin yarım hissettirmesine yol açar.
> * **Ölüm Ekranı / Run Özeti:** Kaç düşman öldürüldü, hangi augmentler seçildi, en yüksek kombo/streak neydi? Bu istatistikler bir Roguelike oyununun temel döngüsüdür.

---

## 📈 Yol Haritası & Öncelik Sıralaması

> [!TODO] Geliştirme Sırası

1. **Ses Entegrasyonu**
   - *Neden:* En az eforla oyundaki vuruş ve ilerleme hissini en çok katlayacak element.
2. **Augment Tooltip Sistemi**
   - *Neden:* Oyuncu neyi seçtiğini anlamazsa yaptığın augment sisteminin bir değeri kalmaz.
3. **Cevher Ara Ödülleri**
   - *Neden:* Altyapı zaten hazır, sadece değer tanımlaması yapılacağı için maksimum 1 saatlik iş.
4. **Ölüm & Run Özeti Ekranı**
   - *Neden:* Oyunun ana döngüsünü (Loop) kapatıp oyuncuyu tekrar oynamaya teşvik eder.
5. **Meta Progression**
   - *Neden:* Mimari olarak en büyük iş, bu yüzden en sona bırakılmalı ama oyuncu bağlılığı için şart.