# Image Captioning 

Bu proje, bir görüntüye bakarak otomatik açıklama (caption) üreten bir yapay zeka modelidir. Model, bilgisayara bir görüntü verildiğinde onun içeriğini anlayarak bunu birkaç kelimeyle ifade eder. 
---

Bu proje, 2025 OBSS Yapay Zeka Staj Yarışması kapsamında gerçekleştirilmiştir. Temel amaç, görsellerin içeriğini anlayıp insan dilinde ifade edebilen bir model geliştirmektir.

- Görsellerin içeriğini otomatik anlamak için **CNN (Convolutional Neural Network)** kullanılmıştır.
- Oluşan bilgileri dilsel açıklamaya dönüştürmek için **LSTM (Long Short-Term Memory)** modeli kullanılmıştır.

---

## Nasıl Çalışıyor?

Modelin çalışma süreci şu adımlardan oluşur:

1. **Caption Verisi Temizlenir:**
   - Küçük harfe çevrilir, noktalama işaretleri temizlenir, “startseq” ve “endseq” gibi belirteçler eklenir.

2. **Görsellerden Özellik Çıkarılır:**
   - Görseller `Xception` adlı hazır bir CNN modeline verilir.
   - Model, her bir görseli 2048 uzunluğunda bir vektör (özellik kümesi) ile temsil eder.

3. **Kelime Sıraları ve Model Girdileri Oluşturulur:**
   - Caption’lar tokenizer ile sayıya çevrilir.
   - LSTM modeli, görsel özelliklerle beraber kelime sıralarını öğrenmeye çalışır.

4. **Model Eğitilir:**
   - Eğitim verisiyle model, bir sonraki kelimeyi tahmin etmeyi öğrenir.
   - Her eğitim adımında hem görsel hem de caption girdisi birlikte verilir.

5. **Tahmin / Caption Oluşturma:**
   - Yeni görsel için model, kelimeleri sırayla tahmin ederek tam bir açıklama üretir.

---

## ⚙️ Kullanılan Teknolojiler ve Kütüphaneler

| Alan | Kullanılan Teknoloji |
|------|-----------------------|
| Görüntü işleme | Pillow (PIL), TensorFlow, Xception |
| Doğal dil işleme | Keras Tokenizer, LSTM, Embedding |
| Derin öğrenme | TensorFlow, tf.keras |
| Veri işleme | Pandas, NumPy |
| Eğitim takibi | tqdm, pickle |

