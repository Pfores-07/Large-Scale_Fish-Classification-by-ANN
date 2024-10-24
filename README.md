# Large-Scale_Fish-Classification-by-CNN
Bu proje, farklı balık türlerini bir Konvolüsyonel Sinir Ağı (CNN) kullanarak sınıflandırmayı amaçlamaktadır. Balık görüntülerinden oluşan bir veri seti kullanılarak 9 farklı balık türünü ayırt edebilen bir model geliştirilmiştir.

Proje Akışı:
1. Veri Seti Hazırlığı:
- Veri seti dizinden yüklenir ve balık türleri, sınıf etiketlerine göre farklı klasörlerde depolanmış görüntülerden oluşur.
- Görüntü yolları ve ilgili etiketler toplanır ve daha fazla işlem için bir Pandas DataFrame oluşturulur.

2. Veri Görselleştirme:
- Balık türlerinin sınıf dağılımı, veri setindeki dengesizliği daha iyi anlamak için çubuk grafiklerle görselleştirilir.
- Her balık sınıfından örnek görüntüler, veri setine genel bir bakış sağlamak amacıyla gösterilir.

3. Veri Bölme ve Ön İşleme:
- Veri seti, eğitim (%80) ve test (%20) olarak train_test_split kullanılarak bölünür ve sınıfların dengeli dağılımını sağlamak için stratifikasyon yapılır.
- Görüntüler, 224x224 boyutuna yeniden boyutlandırılır ve piksel değerleri normalize edilir.

4. Model Mimarisi:
- TensorFlow/Keras kullanılarak çok katmanlı bir Sequential CNN modeli oluşturulur:
- ReLU aktivasyonlu ve MaxPooling ile 3 Konvolüsyonel katman.
- İki tam bağlantılı (Dense) katman ve Dropout ile regularizasyon uygulanır.
- 9 balık türünü sınıflandırmak için Softmax çıkış katmanı.
- Model, Adam optimizasyon algoritması ve kategorik çapraz entropi kaybı ile derlenir.

5. Model Eğitimi:
- Model, eğitim setinde eğitilir ve aşırı öğrenmeyi önlemek için erken durdurma kullanılır. Eğitim verilerinin %20'si doğrulama için ayrılır.
- 20 epoch ile eğitim yapılır ve her iterasyonda 32 görüntü işlenir.

6. Değerlendirme:
- Eğitim sonrasında model, test setinde değerlendirilir ve doğruluk ile kayıp raporlanır.
- Model performansını değerlendirmek için sınıflandırma raporu ve karışıklık matrisi oluşturulur.

7. Yeni Görüntüler Üzerinde Tahmin:
- Ayrı bir balık görüntüsü yüklenir, ön işleme tabi tutulur ve eğitimli modele verilerek tahmin yapılır.
- Tahmin edilen sınıf etiketi, giriş görüntüsü ile birlikte görselleştirilir.

Sonuçlar:
Model, test setinde kayda değer bir doğruluk elde etmiştir. Performans daha iyi hale getirmek için sınıflandırma raporları ve karışıklık matrisleri kullanılarak analiz yapılmıştır.

Kaggle Proje Linki: https://www.kaggle.com/code/urasalkaya/large-scale-fish-classification-by-ann
