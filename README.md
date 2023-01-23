# Laporan Proyek Machine Learning - Muhammad Fadhel Haidar

## Project Overview

Media sosial merupakan salah satu platform yang sangat populer di era digital saat ini. Namun, di balik kepopulerannya, media sosial juga menyimpan berbagai masalah, salah satunya adalah komentar *toxic*. Komentar *toxic* adalah komentar yang menyebarluaskan ujaran kebencian, menyakiti, atau menyebarkan informasi yang tidak benar. Penelitian menunjukkan bahwa komentar toxic dapat menyebabkan efek negatif pada mental dan emosional pengguna media sosial. Hal ini karena komentar toxic dapat menimbulkan rasa tidak aman, kecemasan, dan depresi pada individu yang menerima komentar tersebut [1]. Selain itu, komentar *toxic* juga dapat menyebarluaskan propaganda dan menyebarkan informasi yang salah, yang dapat mempengaruhi opini publik dan menyebabkan kerusakan pada lingkungan sosial.

Sistem deteksi komentar *toxic* di media sosial merupakan solusi penting dalam menangani masalah kekerasan verbal yang terjadi di dunia maya. Dengan menggunakan teknologi *Natural Language Processing* (NLP), sistem ini dapat mengidentifikasi komentar yang memiliki konten negatif, seperti penghinaan, kebencian, atau ancaman. *Natural Language Processing* (NLP) merupakan cara komputer untuk menganalisa, memahami dan memaknai bahasa manusia. Sistem ini juga dapat mengklasifikasikan tingkat keparahan dari komentar tersebut, sehingga dapat memberikan tindakan yang sesuai [2]. Sistem deteksi komentar *toxic* di media sosial dapat menjadi solusi efektif dalam menangani masalah kekerasan verbal di dunia maya. 

Pada sistem yang dibuat kali ini, metode yang digunakan dalam untuk melakukan pendekatan dan penyelesaian masalah adalah 'FastText' dan *Neural Network*. 'FastText' adalah sebuah metode pemrosesan bahasa alami yang menggabungkan teknik-teknik dari kedua metode: *word embedding* dan klasifikasi teks. FastText menggunakan embedding kata yang dibentuk dengan cara mengambil rata-rata dari embedding kata dalam kalimat. Kemudian, embedding kalimat ini digunakan sebagai input untuk jaringan saraf yang digunakan untuk melakukan klasifikasi teks. *Neural network* adalah sebuah metode pemrosesan bahasa alami yang menggunakan jaringan saraf untuk melakukan pemrosesan teks. Neural network dapat digunakan untuk berbagai tipe pemrosesan bahasa alami, seperti klasifikasi teks, penerjemahan, dan pembuatan jawaban. Neural network dapat digunakan untuk mengintegrasikan berbagai jenis data, seperti teks, gambar, dan suara, untuk melakukan pemrosesan yang lebih baik. 

## Business Understanding

Masalah yang telah dibahas sebelumnya adalah komentar toxic yang terjadi di media sosial. Komentar toxic dapat menyebabkan efek negatif pada mental dan emosional pengguna media sosial serta dapat menyebarluaskan propaganda dan informasi yang salah. Solusi yang ditawarkan untuk menangani masalah ini adalah dengan menggunakan sistem deteksi komentar toxic di media sosial yang menggunakan teknologi Natural Language Processing (NLP) dan metode 'FastText' dan Neural Network. 'FastText' digunakan untuk mengambil rata-rata dari embedding kata dalam kalimat dan digunakan sebagai input untuk jaringan saraf untuk melakukan klasifikasi teks. Neural network digunakan untuk melakukan pemrosesan teks dan dapat digunakan untuk mengintegrasikan berbagai jenis data. Bila dilihat dari latar belakang masalah yang sudah dijelaskan sebelumnya, maka didapati pernyataan masalah sebagai berikut:

### Problem Statements

- Mencari nilai _accuracy_ dari model sistem klasifikasi yang dibuat?
- Mencari nilai _loss_ dari model sistem klasifikasi yang dibuat?

### Goals

- Mendapatkan nilai _accuracy_ dari model sistem klasifikasi.
- Mendapatkan nilai _loss_ dari model sistem klasifikasi.
 
     ### Solution statements
     Metode yang digunakan untuk membuat sistem klasifikasi adalah 'FastTex' yang merupakan *pre-trained embedding library* untuk proses *embedding* dari kata-kata      yang akan dilatih, 'FastText' merupakan *pre-trained embedding library* yang dikembangkan oleh *Facebook AI Research (FAIR)* untuk melakuka proses vektorisasi dan      klasifikasi dari data *text* menggunakan metode *n-gram characters* sebagai unit terkecilnya. Tujuan dari pemilihan *FastText* adalah untuk meningkatkan performa      dari model.
    
## Data Understanding

Pada *dataset Toxic Comment Classification* terdapat kolom *id,	comment_text,	toxic,	severe_toxic,	obscene,	threat,	insult,	identity_hate,	non_toxic*
- id : merupakan kolom yang berisikan nomor *id* dari masing-masing data *text*.
- comment_text : merupakan kolom untuk data *text* yang nantinya akan diolah dan dilatih.
- toxic : kolom ini merupakan kolom untuk label atau kelas dari dataset yang berisikan kalimat yang bersifat *toxic.
- severe_toxic : kolom ini merupakan kolom untuk label atau kelas dari dataset yang berisikan kalimat yang bersifat sangat *toxic.
- obscene : kolom ini merupakan kolom untuk label atau kelas dari dataset yang berisikan kalimat yang bersifat cabul atau tidak senonoh. 
- threat : kolom ini merupakan kolom untuk label atau kelas dari dataset yang berisikan kalimat yang bersifat ancaman.
- identity_hate : kolom ini merupakan kolom untuk label atau kelas dari dataset yang berisikan kalimat yang bersifat rasis atau menyangkut SARA.


Berdasarkan analisis data yang telah dilakukan, diperoleh jumlah observasi untuk setiap kategori label yang ditunjukan pada tabel beriku.

| category	 | number of comments |
| :-------------: | :-------------: |
| toxic | 15294 |
| severe_toxic | 1595
| obscene | 8449
| threat	| 478
| insult | 7877
| identity_hate | 1405

###### Tabel 1, Distribusi Data Pada Label

Berikut merupakan visualisasi dari distribusi data. 

![I1QmknU](https://user-images.githubusercontent.com/66835763/214020815-1f6d4078-ad2e-484d-b021-c674da825223.png)
###### Gambar 1, Visualisasi Distribusi Data


Setelah mengidentifikasi label-label yang ada pada data, korelasi antar label dianalisis menggunakan library 'seaborn'. Hasil analisis menunjukkan nilai-nilai korelasi antar label yang diperoleh. Berikuit merupakan hasil visualisasi dari korelasi antar data.

![5bLBzpt](https://user-images.githubusercontent.com/66835763/214021230-4b15cd32-afb1-490b-8451-efd3cdaf9385.png)
###### Gambar 2, Visualisasi Korelasi Data


## Data Preparation
Berdasarkan analisis data yang telah dilakukan sebelumnya, didapatkan bahwa dataset yang digunakan masih mengandung nilai-nilai yang tidak relevan untuk digunakan dalam proses pemodelan. Oleh karena itu, dibutuhkan tahap preparasi dataset yang disebut dengan proses data cleaning untuk menghilangkan nilai-nilai yang tidak diperlukan dan membuat dataset menjadi lebih bersih. Tahapan-tahapan yang dilakukan dalam proses data cleaning ini adalah sebagai berikut :

```
# Conerting all strings into lower case
data["comment_text"] = data["comment_text"].str.lower()

# Replacing non-breaking space with a regular space 
data["comment_text"] = data["comment_text"].str.replace("\xa0", " ", regex=False).str.split().str.join(" ")

# Removing extra spaces in text
data["comment_text"] = data["comment_text"].map(lambda x: re.sub(r"\s\s+", " ",x))

# Removing Hyperlinks from text
data["comment_text"] = data["comment_text"].map(lambda x: re.sub(r"https?://\S+|www\.\S+","",x))

# Removing Special characters 
data["comment_text"] = data["comment_text"].map(lambda x: re.sub(r"[^a-zA-Z0-9\s\"\',:;?!.()]", " ",x))

```
Kode program di atas digunakan untuk melakukan proses pre-processing pada kolom "comment_text" dari data. Proses pre-processing ini dilakukan dengan beberapa tahap sebagai berikut:

- Mengubah semua teks menjadi huruf kecil dengan menggunakan fungsi str.lower() pada kolom "comment_text".

- Mengganti non-breaking space dengan spasi reguler dengan menggunakan fungsi str.replace() dan str.split().str.join().

- Menghilangkan spasi yang berlebih pada teks dengan menggunakan fungsi re.sub().

- Menghilangkan hyperlink dari teks dengan menggunakan fungsi re.sub().

- Menghilangkan karakter spesial dari teks dengan menggunakan fungsi re.sub() dan menyimpan karakter yang diizinkan seperti huruf, angka, tanda baca, dan karakter lain yang diperlukan.


## Modeling
Pada bagian ini, data text terlebih dahulu menggunakan *pre-trained embedding* 'FastTex', kemudian didapatkan nilai total *text* yang telah divektorisasi sebagai berikut.

###### FastTex Vectorization
 ```
999995it [00:55, 17924.62it/s]
Loaded 999994 word vectors.
total embedded: 85984 common word
 ```

Kemudian hasil dari vektorisasi digunakan sebagai input untuk model, berikut mmerupakan hasil *summary* untuk model *nerural network* yang digunakan pada sistem ini.

###### Model Summary
```
Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
embedding (Embedding)        (None, 200, 300)          57044100  
_________________________________________________________________
bidirectional (Bidirectional (None, 200, 128)          187392    
_________________________________________________________________
dropout (Dropout)            (None, 200, 128)          0         
_________________________________________________________________
global_max_pooling1d (Global (None, 128)               0         
_________________________________________________________________
dropout_1 (Dropout)          (None, 128)               0         
_________________________________________________________________
dense (Dense)                (None, 50)                6450      
_________________________________________________________________
dropout_2 (Dropout)          (None, 50)                0         
_________________________________________________________________
dense_1 (Dense)              (None, 6)                 306       
=================================================================
Total params: 57,238,248
Trainable params: 57,238,248
Non-trainable params: 0
_________________________________________________________________
```

Summary di atas menunjukkan arsitektur dari model yang dibuat dan jumlah parameter yang digunakan oleh setiap lapisan. Setiap lapisan ditunjukkan dengan nama lapisan, tipe lapisan, bentuk output, dan jumlah parameter.

1. Lapisan Embedding memiliki output shape (None, 200, 300) dan memiliki jumlah parameter 57044100. Lapisan ini digunakan untuk mengubah token teks menjadi representasi numerik yang dapat diterima oleh model.

2. Lapisan Bidirectional CuDNNLSTM memiliki output shape (None, 200, 128) dan memiliki jumlah parameter 187392. Lapisan ini digunakan untuk menangkap konteks dari teks.

3. Lapisan Dropout memiliki output shape yang sama dengan lapisan sebelumnya (None, 200, 128) dan tidak memiliki parameter. Lapisan ini digunakan untuk mengurangi overfitting.

4. Lapisan GlobalMaxPool1D memiliki output shape (None, 128) dan tidak memiliki parameter. Lapisan ini digunakan untuk mengambil nilai maksimum dari setiap fitur yang dihasilkan oleh lapisan sebelumnya.

5. Lapisan Dense memiliki output shape (None, 50) dan memiliki jumlah parameter 6450. Lapisan ini digunakan sebagai lapisan fully connected yang digunakan untuk mengubah representasi numerik menjadi prediksi klasifikasi.

6. Lapisan Dense memiliki output shape (None, 6) dan memiliki jumlah parameter 306. Lapisan ini digunakan sebagai lapisan output yang digunakan untuk menghasilkan prediksi klasifikasi.

Total jumlah parameter yang digunakan oleh model adalah 57,238,248 dan semua lapisan dapat di-training.

## Evaluation

Pelatihan dilakukan selama 4 epoch atau siklus. Dalam setiap epoch, model diterapkan pada 4488 data latih dan data validasi.

Pada setiap epoch, terlihat bahwa nilai loss (nilai yang menunjukkan seberapa jauh prediksi model dari hasil yang sebenarnya) semakin kecil dan nilai akurasi (persentase data yang diklasifikasikan dengan benar) semakin tinggi. Namun, pada data validasi, nilai loss dan akurasi tidak berubah selama 4 epoch.

Loss pada epoch pertama adalah 0.1036 dan akurasi 0.7810. Pada epoch keempat, loss adalah 0.0438 dan akurasi 0.9770. Hal ini menunjukkan bahwa model semakin baik dalam mengenali dan memprediksi data latih. Namun, karena nilai validasi tidak berubah, ini menunjukkan bahwa model mungkin mulai overfitting (mempelajari data latih dengan sangat baik namun kurang baik pada data baru)

Itu artinya, model sudah cukup baik dalam memprediksi data latih, namun kurang baik dalam memprediksi data baru. Oleh karena itu, perlu ditambahkan data validasi atau diterapkan teknik lain untuk mengurangi overfitting.

```
Epoch 1/4
4488/4488 [==============================] - 147s 32ms/step - loss: 0.1036 - accuracy: 0.7810 - val_loss: 0.0565 - val_accuracy: 0.9940
Epoch 2/4
4488/4488 [==============================] - 147s 33ms/step - loss: 0.0524 - accuracy: 0.9535 - val_loss: 0.0512 - val_accuracy: 0.9940
Epoch 3/4
4488/4488 [==============================] - 145s 32ms/step - loss: 0.0463 - accuracy: 0.9690 - val_loss: 0.0510 - val_accuracy: 0.9940
Epoch 4/4
4488/4488 [==============================] - 145s 32ms/step - loss: 0.0438 - accuracy: 0.9770 - val_loss: 0.0502 - val_accuracy: 0.9940
```

download.png
![download](https://user-images.githubusercontent.com/66835763/214025576-d2e16700-7fb1-4b12-b446-24f88b9df655.png)
###### Gambar 3, Visualisasi Data Latih

###### Hasil Data Uji
```
2000/2000 [==============================] - 16s 8ms/step - loss: 0.0728 - accuracy: 0.9976
Test Loss: 0.07284168154001236
Test Accuracy: 0.9976085424423218
```
Ini adalah hasil pengujian model setelah dilatih. Model diterapkan pada 2000 data uji.

Dari hasil pengujian, dapat dilihat bahwa nilai loss (nilai yang menunjukkan seberapa jauh prediksi model dari hasil yang sebenarnya) adalah 0.0728 dan nilai akurasi (persentase data yang diklasifikasikan dengan benar) adalah 0.9976. Hal ini menunjukkan bahwa model cukup baik dalam mengenali dan memprediksi data uji.

Nilai akurasi yang tinggi menunjukkan bahwa model sudah cukup baik dalam memprediksi data uji. Namun, perlu diingat bahwa nilai ini hanya menunjukkan hasil pada data uji yang digunakan saat ini, dan belum tentu menunjukkan hasil yang sama pada data uji yang berbeda atau data baru.


###### Testing Menggunakan *Text*
```
your blatant pov pushing neither of you guys has made any contribution to this italian history article other than to shove your unhistorical unconstructive modern pov in my face. this is a history article. history. have you heard of that? this is the reason why so many people get pissed off about the pedantry and idiocy and triviality of wikipedia. j sus. get a f cking life.
{'toxic': 0.98362917, 'severe_toxic': 0.06779731, 'obscene': 0.89391726, 'threat': 0.0013799085, 'insult': 0.5765569, 'identity_hate': 0.011462662, 'non_toxic': 0.00090842607}
Actual Values: {'toxic': 1, 'severe_toxic': 0, 'obscene': 1, 'threat': 0, 'insult': 0, 'identity_hate': 0, 'non_toxic': 0}
```
Hasil di atas adalah hasil dari proses klasifikasi teks oleh model yang digunakan untuk mengidentifikasi tingkat *toxicity* dalam teks. Teks yang digunakan adalah sebuah komentar yang mengkritik penyuntingan artikel sejarah Italia di Wikipedia.

Model mengeluarkan nilai prediksi untuk setiap kategori, yaitu:

toxic: 0.98362917 (98.36% kemungkinan teks tersebut bersifat kekerasan)
severe_toxic: 0.06779731 (6.78% kemungkinan teks tersebut bersifat sangat kekerasan)
obscene: 0.89391726 (89.39% kemungkinan teks tersebut bersifat kasar)
threat: 0.0013799085 (0.14% kemungkinan teks tersebut bersifat ancaman)
insult: 0.5765569 (57.66% kemungkinan teks tersebut bersifat sarkasme atau caci maki)
identity_hate: 0.011462662 (1.15% kemungkinan teks tersebut bersifat diskriminatif)
non_toxic: 0.00090842607 (0.09% kemungkinan teks tersebut bersifat tidak kekerasan)
Kemudian, ditunjukkan juga nilai aktual dari teks tersebut, yaitu:

toxic: 1 (teks tersebut bersifat kekerasan)
severe_toxic: 0 (teks tersebut tidak bersifat sangat kekerasan)
obscene: 1 (teks tersebut bersifat kasar)
threat: 0 (teks tersebut tidak bersifat ancaman)
insult: 0 (teks tersebut tidak bersifat sarkasme atau caci maki)
identity_hate: 0 (teks tersebut tidak bersifat diskriminatif)
non_toxic: 0 (teks tersebut tidak bersifat tidak kekerasan)
Dapat dilihat bahwa model cukup baik dalam mengidentifikasi teks tersebut sebagai bersifat kekerasan dan kasar, namun kurang baik dalam mengidentifikasi teks tersebut sebagai bersifat sarkasme atau caci maki.

## Kesimpulan

## Daftar Referensi
[1]  I. Pantic, “Online social networking and Mental Health,” Cyberpsychology, Behavior, and Social Networking, vol. 17, no. 10, pp. 652–657, 2014. 

[2]  Lopez, M.M. and Kalita, J. (2017) Deep learning applied to NLP, arXiv.org. Available at: https://doi.org/10.48550/arXiv.1703.03091 (Accessed: January 23, 2023). 
