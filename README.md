# Pusula_Batuhan_Simsek  
**Pusula Data Science Intern Case Study**  

Batuhan Şimşek  
batuhansimsek203@gmail.com  

---

##  Proje Hakkında  
Bu çalışma, **Pusula 2025 Data Science Intern Case** kapsamında verilmiş veri seti üzerinde gerçekleştirilmiştir.  
Amaç, **Tedavi Süresi (TedaviSuresi)** hedef değişkeni etrafında veriyi analiz etmek, temizlemek ve modellemeye hazır hale getirmektir.  

---

##  Adımlar  

### 1. Veri Yükleme  
- Google Colab ortamında `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn` kütüphaneleri yüklendi.  
- Orijinal Excel dosyası `read_excel()` ile içe aktarıldı.  

---

### 2. Veri Keşfi (EDA)  
- `df.info()`, `df.describe()`, `df.isna().sum()` ile veri seti incelendi.  
- Eksik değer dağılımları çıkarıldı.  
- Kategorik değişkenlerin dağılımları barplot ile görselleştirildi (`Cinsiyet`, `KanGrubu`, `Uyruk` …).  
- Sayısal değişkenlerin dağılımları histogram ve boxplot ile incelendi.  

---

### 3. Veri Ön İşleme  

#### 3.1 Sayısal Kolonlar  
- `TedaviSuresi` kolonundaki **"Seans"** ifadesi çıkarıldı → `TedaviSuresi_Seans`  
- `UygulamaSuresi` kolonundaki **"Dakika"** ifadesi çıkarıldı → `UygulamaSuresi_Dakika`
- Bu sayede değerler numerik hale gelirken okunurluk kaybedilmedi.

#### 3.2 Alerji Sütunu  
- Eksik değerler `"Bilinmiyor"` olarak dolduruldu.  
- Harf standardizasyonu ve yazım hataları düzeltildi  
  - `TOZ → toz`, `Volteren → Voltaren`, `Gri̇pi̇n → Gripin`.  
- Virgülle ayrılmış değerler listeye çevrildi ve tekrarlayanlar tekilleştirildi.  
- One-hot encoding uygulandı → her alerji türü için ayrı sütun (`polen`, `toz`, `voltaren` …).  

#### 3.3 Uygulama Yerleri  
- Virgülle ayrılmış bölgeler listeye dönüştürüldü.  
- One-hot encoding ile her bölge ayrı sütun haline getirildi (`boyun`, `sırt`, `diz` …).  

#### 3.4 Cinsiyet ve Kan Grubu  
- Eksik değerler `"Bilinmiyor"` ile dolduruldu.  
- One-hot encoding uygulandı  
  - `cinsiyet_Erkek`, `cinsiyet_Kadın`, `cinsiyet_Bilinmiyor`  
  - `kangrubu_0 Rh+`, `kangrubu_AB Rh-`, `kangrubu_Bilinmiyor` …  

#### 3.5 Drop Edilen Sütunlar  
- `KronikHastalik`, `Bolum`, `Uyruk` → hedef değişkenle doğrudan ilişkili olmadığı ve çok gürültülü olduğu için çıkarıldı.  
- `TedaviAdi` sütunu → bölgelere göre yeniden düzenlendi.  

---

### 4. Sayısal Kolonlar Üzerine Notlar  
- `Yas`, `TedaviSuresi_Seans`, `UygulamaSuresi_Dakika` → sayısal değişkenlerdir.  
- Yaş için anormal bir outlier değer bulunmamıştır. TedaviSuresi_Seans ve UygulamaSuresi_Dakika için de anormal ve sıradışı bir outlier değere rastlanmamıştır.  

---

### 5. Sonuç  
- Tüm kategorik ve çoklu kategorik sütunlar encode edilmiştir.  
- Eksik değerler uygun şekilde doldurulmuştur.  
- Gereksiz sütunlar çıkarılmıştır.  
- Ortaya çıkan veri seti **modellemeye hazır hale getirilmiş** ve **Excel dosyası** olarak kaydedilmiştir.  

---

##  Çalıştırma  
1. Gerekli kütüphaneleri yükleyin:  
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn openpyxl

2. Notebook dosyasını çalıştırın.

3. final.xlsx dosyası düzenlenmiş ve modellemeye hazır dosya olarak oluşturulacaktır. İster xlsx, ister csv olarak kullanılabilir.  
