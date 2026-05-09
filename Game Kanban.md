---

kanban-plugin: board

---

## TO DO

- [ ] experience alma ve level mantigini duzenle.
- [ ] hammerslam de ortaya cikan yildirim cubuklari 4-8 yon arasinda cikar ve transform.translate seklinde dagilir.
- [ ] Katlarda wave mekanigi olustur ve uygula
- [ ] level design 5 kat
- [ ] dilek kuyularina bir altin atip random bir buff alinabilir


## DOING



## Augments

- [ ] Hasarını %100 artırır ancak maksimum canını yarıya indirir.
- [ ] dash skili eklenebilir ve her bir guclendirmede dash skilinin cooldownu azalabilir veya mesafesi artabilir
- [ ] +1 augment slot
- [ ] Replace your bow with a crossbow. Your bow strikes are now automatic.
- [ ] Replace your crossbow with a shotgun. Your crossbow shots are now automatic.
- [ ] Health+
- [ ] Luck +


## Augment popping algorithm

- [ ] with each level there will be 1 common 1 rare and 1 wildcard that will increase in possibility of rarity with every level. (yuzde 95 kontrol yani sikici)
- [ ] agirlikli secim kurulcak.
	
	3 adet common + rare + wildcard havuzu kurulacak. 
	her birisine ait augmentlere bir agirlik tanimlanicak.
	
	Agirlik wildcard slotu icin geceri olacak.
	r = Random(0, totalweight)
	uretildikten sonra gerekli parametrelerce wildcard slotu birikmis weight e gore dolacak.
- [ ] X leveldir epic çıkmadıysa epic ağırlığını artır.
- [ ] - Synergy bias: oyuncunun build’ine uygun augmentlerin ağırlığını +%N artır.
- [ ] - Recency penalty: son 2 levelde çıkan augmentlerin ağırlığını düşür.
- [ ] - Seeded random: debug/test için aynı seed ile aynı sonuç.


## DONE

- [ ] kirilabilir duvarlardan uygun lootlar
- [ ] belirli fonksiyonlari augment alma tarzi yap
- [ ] level up da hammer charge meter tekrar dolu hale gelmiyor.
- [ ] ana karakterin pngsini ve animasyonlarini yenile.
- [ ] hammer charge aktifken oyuncunun damage almasini yuzde x azalt.
- [ ] Projectile magelerin altinda birikiyor. Pooler a aktarmamiz lazim.
- [ ] level up sonrasi butun barlar fullencek
- [ ] bow safi sol tik da charge in calismasini istemiyorum. Mouse a 1 saniyeden fazla sol tiki tutarsan bow charge i calistir seklinde bir sey yapmamiz lazim.
- [ ] damage aldiktan sonra 0.2 sn dokunulmazlik
- [ ] gold count ui ve level count ui
- [ ] can ve experience bar
- [ ] hammer charge icin bar
- [ ] Camera shake
- [ ] [[enemy movement]]
- [ ] dungeon mobility 1.5x
- [ ] Transition effect (black screen)
- [ ] visual feedback : hit stop
- [ ] sag tika bow koy, arrowlarin ucundaki collider a sart ver eger wall a degerse dursun eger enemy ye degerse ucsun ve parcalansin
- [ ] mage enemy class
- [ ] hammercharge da arrow instantiate ediliyor.
- [ ] 2 more enemy types


## BUGS

- [ ] enemyler diger enemylerin lineofsight ini kapatiyor. Onu duzelt.
- [ ] sag sol tik i ayni anda alabiliyosun. Bunu augmente cevirebiliriz.
- [ ] bir kattan diger kata gecerken veya baslangica geri donerken altinlar da sahne degistiriyor. Altinlarin o kata ozgun yap ve diger katlara tasinmamasini sagla.




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,false,true,true]}
```
%%