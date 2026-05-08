## . "Juice" / Game Feel — En Önemli Katman

Vuruş anındaki tatmin tamamen "juice" denilen şeyle ilgili. Mekanik güçlü olsa da juice yoksa boş hisseder. Oyunun zaten `CinemachineImpulse` var — bu iyi bir başlangıç ama bunun %10'u.

Öğrenmен gereken kavramlar:

- Hitstop (Hit Freeze): Vuruş anında oyunu 2-4 frame dondurmak. En ucuz, en etkili feedback tekniği. `Time.timeScale = 0` → kısa bir süre sonra `1`. Binlerce AAA oyunu bunu kullanır.
- Screenshake: Zaten var ama parametreleri doğru ayarlamak önemli — yön, süre, kuvvet dengesi.
- Hit Flash: Düşman vurulduğunda 1-2 frame'lik beyaz parlama. Senin `HitFlashRoutine`'in var zaten, bu iyi.
- Particle Systems: Unity'nin Particle System modülü. Kan, duman, enerji patlamaları. AOE çekiç için zemin çatlama efekti hayal et.
- Damage Numbers: Vuruşta uçan sayı. Critic vurda daha büyük, farklı renk. Görsel bilgi + dopamin ikilisi.
- Death VFX: Düşman ölürken sadece `SetActive(false)` değil — bir patlama, yavaş düşme, eriyip gitme.
- Sound Design: Bu tek başına bir disiplin ama şunu bil: sesin _katmanlı_ olması lazım. Hafif vuruş = ince ses. Ağır çekiç = derin, yankılanan ses. Aynı sesi tekrar etmek bile rahatsız eder — pitch variation şart.

İzlemen gereken:

- "Juice it or Lose it" — Martin Jonasson & Petri Purho (YouTube'da var, 15 dakika, zorunlu)
- "The Art of Screenshake" — Jan Willem Nijman (GDC 2013)
- "30 Things I Hate About Your Game" — Jonathan Blow değil, Phil Fish GDC konuşması

---

## 2. "Oyunu Kırabilmek" — Roguelike Build Tasarımı

Risk of Rain 2, Binding of Isaac, Hades, Slay the Spire. Bu dört oyunu oyna ve _neden_ o hissi yarattıklarını gözlemle. Ortak nokta:

Synergy: Augmentler birbirini çarpan olarak büyütmeli, toplamalı değil. Senin sisteminde şu an toplamalı çalışıyor (hız +%10, +%10). Eğer bir augment _diğer augmentin etkisini ikiye katlarsa_ build exponential büyür ve "kırılma" hissi yaşanır.

Öğrenmеn gerekеn kavramlar:

- Multiplicative vs Additive scaling: Additive = `A + B + C`. Multiplicative = `A × B × C`. İkincisi geç oyunda exponential güç verir.
- Build Identity: Her build kombinasyonu bir playstyle yaratmalı. "Ok build" vs "çekiç build" vs "hız build" birbirinden hissettiren şeyler olmalı.
- Emergence: Tasarlamadığın ama augment kombinasyonlarından ortaya çıkan güçlü build'ler. Bunlar kasıtlı veya kazara olabilir ama oyuncular bunları keşfettiğinde viral olur.
- Power Spike: Belirli bir augment kombinasyonunu tamamladığında oyuncunun gücünün birden sıçraması. Bu an bir "aha!" momenti. Tasarımın içine göm.

Okumаn gereken:

- Binding of Isaac yaratıcısı Edmund McMillen'ın item design felsefesi (röportajlarda anlatıyor)
- Risk of Rain 2'nin item synergy tasarımına dair GDC konuşması var

---

## 3. Ödül Psikolojisi

Variable Ratio Reinforcement Schedule: Slot makinesinin çalışma prensibi. Sabit aralıkta ödül vermek yerine _tahmin edilemez aralıkta_ vermek bağımlılık yaratır. Gold drop chance'in zaten `0.15f` ile bunu yapıyor — ama bunu bilinçli tasarlamak başka bir şey.

Öğrenmен gerekен kavramlar:

- Skinner Box: B.F. Skinner'ın davranış psikolojisi. Oyun tasarımcıları bunu ödül sistemleri için kullanır.
- Escalating Rewards: Süre geçtikçe ödüller büyümeli. Kat 1'de küçük augment, Kat 5'te rare augment. Oyuncu "ne geleceğini merak ediyorum" durumunda kalmalı.
- Sunk Cost + Momentum: Oyuncu bir build'e ne kadar yatırım yaparsa o kadar devam etmek ister. Bu yüzden build identity önemli — augmentler birikince oyuncu o build'i "terk etmek" istemez.
- Feedback Loop: Güçleniyorum → daha kolay öldürüyorum → daha hızlı ödül alıyorum → daha da güçleniyorum. Bu döngünün _hızlanması_ gerekiyor, yavaşlamaması.

Okuман gereken:

- "A Theory of Fun for Game Design" — Raph Koster (kitap, kısa)
- "Flow: The Psychology of Optimal Experience" — Csikszentmihalyi (zorluk = beceri dengesi, bu senin oyunun için kritik)

---

## 4. Unity'de Teknik Olarak Neler Öğrenmen Lazım

Mevcut koduna bakınca eksik olan katmanlar:

|Sistem|Unity'de nasıl öğrenirsin|
|---|---|
|Hitstop|`Time.timeScale` + `IEnumerator`, 3 satır kod|
|Particle System|Unity resmi dokümantasyonu + "Unity VFX Tutorial" araması|
|Damage Number|TextMeshPro + world space canvas + animation|
|Sound (katmanlı)|Unity Audio Mixer + pitch randomization|
|Screen flash (post-process)|Unity URP Post Processing → Bloom, Chromatic Aberration|
|Death VFX|Particle burst + Object pooling (zaten pooler'ın var)|

---

## Öncelik Sırası

Eğer sıfırdan öğrenmeye başlıyorsan ve hangi sırayla çalışacağını bilmiyorsan:

1. "Juice it or Lose it" videosunu izle — tüm resmi görürsün, 15 dakika
2. Hitstop ekle — 10 satır kod, farkı hemen anlarsın
3. Damage number ekle — görsel bilgi + tatmin
4. Sound design — sesin nasıl katmanlandığını anla, Unity Audio Mixer öğren
5. Particle Systems — Unity'de en derin sistemlerden biri, önce basit bir "hit burst" yap
6. Build synergy — bunu kodlamadan önce kağıt üzerinde tasarla: "hangi iki augment birleşince exponential olur?"

---

Kısaca: game feel = juice + sound + visual feedback, build tatmini = multiplicative synergy + power spike tasarımı, ödül döngüsü = variable reward + escalation + feedback hızı. Bunların hepsi ayrı öğrenme alanı ama birbirini besliyor.