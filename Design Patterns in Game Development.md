**Observer Pattern**

Sistemdeki bagimliligi azaltmayi hedefler (coupling).

Unity'de 2 farkli yontemi vardir.

![[Ekran Resmi 2026-05-10 15.07.30.png]]

Diyagramda oldugu gibi bir observer eklenir.
Observer bir interface olarak eklenir. Subjectten gelen bildirimleri dinler. 

public interface IObserver {
    void OnNotify();
}

public class Subject : MonoBehaviour {
    private List<IObserver> observers = new List<IObserver>();

    public void AddObserver(IObserver observer) => observers.Add(observer);
    
    public void Notify() {
        foreach (var observer in observers) {
            observer.OnNotify();
        }
    }
}


Events yontemi ise unity de en yaygin kullanilan bicimdir. Ornegin player olur ve player in oldugunu events sistemi dinleyen butun observerlara iletir. 

using System;
using UnityEngine;

public class PlayerHealth : MonoBehaviour {
    // Subject rolü
    public static event Action OnPlayerDeath;

    public void TakeDamage(int amount) {
        // ... can azaldı ve öldü diyelim
        OnPlayerDeath?.Invoke(); // Tüm abonelere haber ver
    }
}



Observer pattern neden kullaniriz?

- loose coupling en onemli sebebidir. Birden fazla modulun haberlesmesini saglamanin en kolay yollarindan bir tanesidir.
- kodlarin birbirine girmesini engellersin
- oyuna yeni bir ozellik eklenmesi gerektiginde mesela belirli bir event de ses efekti calmasi buna ornek gosterilebilir. Mevcut kodun hicbirisini degistirmene gerek kalmadan yeni bir observer eklemek yeterli olur.||
  
  Unity kullanim senaryolari
- Basarim sistemi
- arayuz guncellemeleri ve ses yonetimi
	  
	  

