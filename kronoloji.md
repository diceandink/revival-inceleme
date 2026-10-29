# Kronoloji

İncelemenin başlangıcından bugüne kadar olan olaylar, özet halinde.
Kişisel veri, özel yazışma ve isim içermez.

---

## 1.

26 Ekim gecesi, bir süre önce Twitter'da görüp nostalji için indirdiğim
Revival projesini incelemeye karar verdim. Eski bir Goley oyuncusuydum;
gönüllü bir ekip çocukluğumuzun oyununu yeniden canlandırmıştı.

Merak ettiğim şey güvenlik değildi: **orijinalin üzerine ne eklemişler?**
Bu sorunun cevabı, oyunun bugünkü haliyle ne kadar orijinal olduğunu da
gösteriyordu.

İlk saatler IDA'da geçti. 54 bin fonksiyon vardı, çoğu Qt'ye aitti; ama
uygulamanın kendi kodu `.text` bölümünün başında toplanmıştı. Kimlik
doğrulama, cihaz anahtarı, oturum, yama ve oyun başlatma akışını buradan
çıkardım.

Sonra Frida ile çalışma zamanına baktım: hangi fonksiyon neyi çağırıyor,
hangi veri ağa çıkıyor. Yalnızca okudum; hiçbir dosyayı değiştirmedim.

Kimlik doğrulama akışını haritalarken istek gövdesinde `hardware` adlı bir
nesne gördüm: anakart ve disk seri numaraları, sistem UUID'si, MAC adresi. Anlaşılan yasaklanan bir oyuncunun hemen yeni hesap açmasına bir önlem alınmak istenmişti. Siteye girip gizlilik metnini kontrol ettim, tahmin ettiğim üzere baştansavma ve eksikti. 

Bunun kötü niyetten çok, küçük bir ekibin ilk projesinde bu işe yeterince
vakit ayıramamasından kaynaklandığını düşündüm. Hâlâ da öyle düşünüyorum.

İncelemeyi derinleştirmedim; 27 Ekim öğlen, ilgimi çeken kısımda kurcalanacak
bir şey kalmayınca bıraktım.

---

## 2.

Raporu iletmek istedim. Disleem'e topluluktan bir
aracı üzerinden başlıkların olduğu ekran görüntüsünü gönderdim. Devamındaki süreçte rapora bile bakmadan yalnızca konu başlıklarıyla gerek olmadığı, boş olduğu yanıtını aldım. Sinirlendim ve Disleem ile discorddan karşılıklı küfürleştik ve discorddan banlandım.

---

## 3. 

Bir şey yapmam gerektiğini düşündüğüm için launcher'ın donanım kimliklerini okuması konusunu gündeme getirmeye karar verdim. Gitgide işi abartarak Twitter'da ufak bir yaygara kopardım ve her yöne çekilebilecek, tam olarak neyi kastettiğimin anlaşılamayacağı tweetler attım. Birkaç oyuncu konuyu aldı ve büyüttü. Sonrası hepinizin malumu, Revival ekibi süreci yönetebilecekleri en berbat şekilde yönetti. Ekibin birbiri ardına duyuru yayınlayıp oyunu bakıma almaları tüm odağı bu konuya çevirdi, oyuncuların kafası karıştı ve oyun bakıma girdi.

Gece saatlerinde merak edip tekrar baktım, olayın community arasında gereğinden fazla büyüdüğünü fark ettim. Ortada zararlı yazılım yoktu, mazur görülebilecek hatalar ve eksiklikler vardı, ama kötü niyetli ve ciddi bir şey değildi. 

O noktada biraz olsun yardımcı olmak için ne yapabilirim diye düşündüm. Ne olursa olsun, küfürleşmiş de olsak Disleem neredeyse tek başına, çalıştığı halde kendisine ayırması gereken kısıtlı vaktini gönüllü olarak bu projeye ayırmış, emek vermişti.

---

## 4.

Discord üzerinden Disleem ile iletişime geçtik. yaptık; iki taraf da kendi hatasını kabul etti.

İlgili paylaşımları kaldırdım. Discord'da bir soru cevap etkinliği yaptık. 

Bir insanın, x bir şeye karşı olan güvenini yıkmak, güven kazanmaktan çok daha kolay, bu yüzden insanlar aynı gün içinde 180 derece dönmemi sorguladı, yapacak bir şey yok, ani parlayıp ani sönüyorum, onlar da haklı o yüzden. Yaptığım şeyi düzeltmek için elimden geleni yaptım. 

---