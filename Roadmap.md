**1. Karakter Kontrolü ve Yerçekimi (Core)**  
Sandbox'ta ilk çözmen gereken şey yerçekimi değiştiğinde karakterin `Velocity` değerinin nasıl korunacağıdır.  

- **Yanlış:** Sadece `Rigidbody2D.gravityScale` değerini `-1` yapmak. Bu, havada asılı kalma hissi yaratır ve kontrolü zorlaştırır.  
    
- **Doğru:** Yerçekimi değiştiği an dikey hızı sıfırlayıp anlık bir ivme (impulse) vermek veya sabit bir düşüş hızı belirlemek. VVVVVV'de hız sabittir, ivmelenme azdır. Bunu netleştir.  
    

**2. State Machine Genişletme**  
Şu anki `GroundedState` yetersiz. Yerçekimi tersine dönebildiği için "Grounded" artık hem tavan hem taban demektir.  

- **Eklemen gerekenler:** `FlippingState` (geçiş anı), `FallingState` (boşlukta olma) ve `DeadState`.  
    
- **Öneri:** `IPlayerContext` üzerinden yerçekimi yönünü bir `Enum` (Up, Down) olarak tut ve State'leri buna göre tetikle.  
    

**3. Ölüm ve Checkpoint Sistemi (Zaman Kaybetmeden)**  
Bu tarz oyunlarda oyuncu çok sık ölür.  

- Sandbox aşamasında `IDamageable` interface'ini kullanarak "Tek vuruşta ölüm" ve "En son checkpoint'e anlık ışınlanma" mekaniğini kurmalısın. Bu kurulmadan level dizaynı test edilemez.  
    

**4. Buff Sistemi (Rage & Speed)**  
Dosyalarında `Rage` ve `Speed` ayrı scriptler olarak duruyor.  

- **Mimari:** Bunları `StatusEffect` gibi bir base class'tan türet.  
    
- **SO Bağlantısı:** `PlayerStats` SO'su "Base" verileri tutmalı, bufflar ise "Runtime" (çalışma zamanı) değerlerini modifiye etmeli. Orijinal veriyi asla ezme.  
    

**5. Level Tasarım Araçları**  
Sandbox'tan hemen sonra Tilemap ve Trigger sistemini kur.  

- Gravity Inverter'ları (yerçekimi çevirici alanlar) `Trigger` olarak tasarla. `OnTriggerEnter2D` içinde `Player` üzerindeki yerçekimi fonksiyonunu çağırsın.  
    

Soru: Vuruş mekaniği (Rage dahil) menzilli mi olacak yoksa yakın dövüş mü? Yerçekimi değişkenken yakın dövüş (melee) hitbox yönetimi zordur.