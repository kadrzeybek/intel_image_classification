# CNN Model and Intel Image Classification Dataset

## Projenin Linki
- [Intel Image Classification Dataset](https://www.kaggle.com/code/kadrzeybek/intel-image-classification)


## Projenin Amacı
Bu projenin amacı bir CNN yapay zeka modeli oluturarak bu modeli Intel Image Classification veri setinini ile eğitmek ve model hakkında değerlendirmeler yapmaktır.

## Veri Seti
- **Kaynak:** [Intel Image Classification Dataset](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)
- **Dataset Türü:** Multiclass Image Classification (6 sınıf)
- **Sınıflar:** Buildings, Forest, Glacier, Mountain, Sea, Street

## Kullanılan Yöntemler
- **Model:** Convolution Neural Network (CNN)
  - Birden fazla **Conv2D ve MaxPooling** katmanı
  - **Dense (Fully Connected)** katmanlar
  - **Dropout** ile overfitting önleme
- **Ön İşleme**
  - Piksel değerlerini 0–1 aralığına normalize etme (normalization)
  - Veri artırma da "ImageDataGenerator" kullanılmıştır (Augmentation)
- **Optimizasyon**
  - Adam Optimizer
  - Loss : Sparse Categoritical Crossentropy
  - Metric: Accurary
  - **Early Stopping** ile aşırı öğrenme engellenmiştir
  - **Hipermetre Optimizasyonu:** farklı learning rate ve bach size'lar ile test edilmesi
- **Modelin Açıklanabilirliğ:**
    - **Eigen-CAM** yöntemi ile modelin hangi bölgeler dikkat ettiğini gösterme

## Elde Edilen Sonuçlar
- Eğitim ve doğrulama seti üzerinde yüksek doğruluk oranı elde edilmiştir.  
- **Classification Report** ve **Confusion Matrix** ile sınıf bazlı performans analiz edilmiştir. 
- **Eigen-CAM görselleştirmeleri**, modelin doğru tahminlerde gerçekten ilgili bölgelere odaklandığını göstermektedir.  
- Hiperparametre optimizasyonu sonucunda:
  - En iyi **Learning Rate** ve **Batch Size** kombinasyonu belirlenmiştir.
 
## Çıktılar
- Train için **11230** adet görsel kullanılmıştır.
- Validation için **2804** adet görsel kullanılmıştır.
- Test için **3000** adet görsel kullanılmıştır.
- Yüksek epoch sayısı veridğimde belirli bir yerde early stop sayesinde durdu.
- Modelin en yüksek **Validation Accuracy:** 83.10
- Modelin en yüksek **Test Accurary:** 82.40
- Train ve Validation Loss grafiğine baktğimizde modelin 10-12. epochta en iyi durumda olduğnu görüyoruz. Sonrasında validation loss artıyor ve overfitting başlıyor.
- Train ve Validation Loss grafiğine baktğimizde modelin 10-11. epochta en iyi durumda olduğnu görüyoruz.
- Farklı bach size ve learning rate denemelerinde **En iyi kombinasyon:** learning rate = 0.1, batch size= 64
