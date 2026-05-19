# Medical Appointment Project 

Bu proje, hastaların tıbbi randevularına gelmeme durumlarını (No-show) etkileyen faktörleri analiz etmek amacıyla geliştirilmiştir. Proje, veri temizleme ve analiz olmak üzere iki ana aşamadan oluşmaktadır.

---

##  1. Veri Ön İşleme ve İlk Analiz (`anlam.ipynb`)
Bu aşamada Kaggle veri seti okunmuş, temizlenmiş ve temel analizler gerçekleştirilmiştir:
* **Veri Temizleme:**
  * Tarih formatları (`datetime`) standart hale getirilerek analiz edilebilir hale getirilmiştir.
  * Yaşı 0'dan küçük olan hatalı satırlar ve mantıksız negatif bekleme süreleri temizlenmiştir.
  * `Handcap` sütunundaki yazım hatası `Handicap` olarak düzeltilmiştir.
* **Özellik Mühendisliği (Feature Engineering):**
  * Randevu bekleme süreleri hesaplanmış ve anlamlı kategorilere ayrılmıştır (`wait_group`: *Aynı Gün, 1-7 Gün, 7-30 Gün, 30+ Gün*).
  * Randevuların haftanın hangi gününe denk geldiği belirlenmiştir.
* **Analiz ve Bulgular:**
  * Bekleme süresi arttıkça randevuya gelmeme oranının arttığı tespit edilmiş ve bu durum grafiklerle görselleştirilmiştir.
  * Temizlenen ve sadeleştirilen veri, sonraki analizler için `cleaned_medical_appointments.csv` adıyla kaydedilmiştir.

---

##  2. SMS Etki Analizi (`sms.ipynb`)
Temizlenmiş veri seti üzerinden SMS gönderiminin hastaların randevuya katılımına etkisi incelenmiştir:
* **Genel SMS Etkisi:** SMS gönderiminin, genel olarak randevuya gelmeme riskini **%1.9 puan** düşürdüğü hesaplanmıştır.
* **Bekleme Süresine Göre SMS Etkisi:** Bekleme süresi uzadıkça SMS'in koruyucu etkisinin belirgin şekilde arttığı görülmüştür:
  * 30 günden fazla bekleyen hastalarda SMS gönderimi, gelmeme oranını **%7.2 puan** azaltmaktadır.
* **Görselleştirme:** Elde edilen bulgular çubuk grafiklerle desteklenerek analiz sonuçları görselleştirilmiştir.

---

##  Öne Çıkan Bulgular (Insights)
1.  **Bekleme Süresi:** Randevu tarihi ile planlama tarihi arasındaki süre uzadıkça hastaların randevuyu kaçırma olasılığı artmaktadır.
2.  **SMS Hatırlatmaları:** SMS gönderimi özellikle uzun vadeli randevularda (7 günden fazla bekleyenler) katılımı artırmada kritik bir rol oynamaktadır.