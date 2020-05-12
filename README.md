# Penggunaan Spark MLlib dan Spark Compiled Model

<hr>

## Referensi fungsi tiap-tiap node

- **Create Local Big Data Environment**: berfungsi untuk membuat environment big data yang memuat Apache Hive, Apache Spark, dan HDFS.
- **File Reader**: berfungsi untuk membaca file.
- **Table to Spark**: berfungsi untuk membuat Dataframe pada Spark dari KNIME data table
- **Spark k-Means**: berfungsi untuk mengaplikasikan algoritma K-means clustering pada Apache Spark.
- **Spark MLib to PMML**: berfungsi untuk mengubah model Machine Learning menjadi Predictive Model Markup Language
- **PMML Compiler**: berfungsi sebagai compiler Predictive Model Markup Language yang diterima dalam Java bytecode
- **Compiled Model Predictor**: berfungsi untuk menjalankan hasil model yang telah di-compile dengan data yang ingin diprediksi
- **Entropy Scorer**: berfungsi untuk mengevaluasi model prediksi menggunakan entropy
- **Container Input (JSON)**: berfungsi untuk menerima input dalam format JSON
- **Container Output (JSON)**: berfungsi untuk mengeluarkan output dalam format JSON
- **JSON to Table**: berfungsi untuk mengkonversi data JSON menjadi baris pada tabel
- **Table to JSON**: berfungsi untuk mengkonversi data baris pada tabel menjadi format JSON
- **Spark Compiled Model Predictor**: berfungsi untuk menjalankan hasil model yang telah di-compile dengan data yang ingin diprediksi dalam skala besar.
- **Decision Tree Learner**: berfungsi untuk melakukan klasifikasi menggunakan metode decision tree.
- **RProp MLP Learner**: berfungsi untuk membuat model prediksi Neural Network menggunakan algoritma RProp.
- **PMML To Cell**: berfungsi untuk mengkonversi model menjadi table cell.
- **Concatenate**: berfungsi untuk menggabungkan tabel.
- **Table to PMML Ensemble**: berfungsi membentuk Predictive Model Markup Language dari data pada tabel dengan menggabungkan beberapa algoritma Machine Learning.
- **Spark to Table**: berfungsi untuk mengkonversi spark dataframe menjadi data pada tabel KNIME.
- **Scorer**: berfungsi untuk mengevaluasi hasil prediksi dengan confusion matrix

# Mass Learning Event Prediction MLib to PMML (Iris Dataset)

<hr>

![Workflow1](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/workflow1.jpg)

## _Business Understanding_

### Kemungkinan proses yang dapat dilakukan dari data

- Mempercepat dalam klasifikasi jenis bunga
- Mencari pengecualian di dalam dataset

## _Data Understanding_

![Data Set](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/dataset.jpg)

- jumlah data training sebanyak **75 baris**
- jumlah data test sebanyak **75 baris**

- sepal length: panjang **kelopak bunga** dalam cm
- sepal width: lebar **kelopak bunga** dalam cm
- petal length: panjang **daun bunga** dalam cm
- petal width: lebar **daun bunga** dalam cm
- class: klasifikasi **kelas iris**

## _Data Preparation_

![Convert table to spark](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/converttospark.jpg)

Melakukan konversi dari data yang telah di-load pada tabel menjadi Spark dataframe menggunakan **Table to Spark**

## _Modelling_

![Model](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/modelinspark.jpg)

### Proses modelling:

1. Data yang telah di-load dan dikonversi menggunakan **Table to Spark** selanjutnya diproses menggunakan **Spark k-Means** untuk mendapatkan model dari hasil training.
2. Dari model yang didapatkan melalui Spark, selanjutnya dengan Node **Spark MLlib to PMML** akan dikonversi menjadi model yang universal berupa **Predictive Model Markup Language**, yaitu suatu standard yang digunakan untuk merepresentasikan model prediksi.
3. Setelah didapatkan model dalam bentuk **Markup**, model dapat di-compile menggunakan **PMML Compiler** agar bisa digunakan untuk memprediksi data testset dengan format yang diinginkan.

- **Format File**:<br>
  ![File Load](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/fileprediction.jpg)<br>

  1. File dibaca menggunakan **File Reader**.
  2. Model yang telah di-compile sebelumnya dapat digunakan untuk memprediksi data test dengan menggunakan **Compilled Model Predictor**.

- **Format JSON**:<br>
  ![JSON Load](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/jsonprediction.jpg)<br>
  1. Input dimasukkan ke dalam **Container Input (JSON)**. <br>
     ![JSON Input](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/jsoninput.jpg)<br>
  2. Data dalam format JSON dikonversi dengan menggunakan **JSON to Table** terlebih dahulu.
  3. Model yang telah di-compile sebelumnya dapat digunakan untuk memprediksi data test dengan menggunakan **Compilled Model Predictor**.
  4. Data hasil prediksi dikembalikan menjadi format JSON menggunakan **Table to JSON**.

## _Evaluation_

![Entropy Scorer](https://github.com/DJahvoe/ETL-menggunakan-KNIME/blob/master/screenshot/entropyscorer.jpg)<br>
![Quality Table](https://github.com/DJahvoe/ETL-menggunakan-KNIME/blob/master/screenshot/qualitytable.jpg)<br>
Model dievaluasi menggunakan **Entropy Scorer**

## _Deployment_

![Deploy](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/deploy.jpg)<br>
Pada tahap deployment digunakan **Predictive Model Markup Language** yang nantinya dapat diterapkan pada sistem menggunakan **Compiled Model Predictor**.

# PMML to Spark Comprehensive Mode Learning Mass Prediction (Iris Dataset)

<hr>

![Workflow2](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/workflow2.jpg)

## _Business Understanding_

### Kemungkinan proses yang dapat dilakukan dari data

- Mempercepat dalam klasifikasi jenis bunga
- Mencari pengecualian di dalam dataset

## _Data Understanding_

![Data Set](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/dataset.jpg)

- jumlah data training sebanyak **75 baris**
- jumlah data test sebanyak **75 baris**

- sepal length: panjang **kelopak bunga** dalam cm
- sepal width: lebar **kelopak bunga** dalam cm
- petal length: panjang **daun bunga** dalam cm
- petal width: lebar **daun bunga** dalam cm
- class: klasifikasi **kelas iris**

## _Data Preparation_

![Convert table to spark](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/tabletospark2.jpg)

Melakukan konversi dari data yang telah di-load pada tabel menjadi Spark dataframe menggunakan **Table to Spark**, data preparation hanya dilakukan pada data training saja.

## _Modelling_

![Model2](https://github.com/DJahvoe/Spark-Compiled-Model/blob/master/screenshot/modelinspark2.jpg)

### Proses modelling:

1. Data di-load menggunakan **File Reader**.
2. Data yang telah di-load akan di-training dengan model yang diinginkan (dalam kasus ini menggunakan **Decision Tree** dan **RProp MLP**).
3. Setelah model terbentuk dalam format PMML, dikonversi menjadi bentuk tabel dengan menggunakan **PMML To Cell**.
4. Untuk kasus ini, karena terdapat 2 model, kedua model dapat digabungkan menggunakan **Concatenate** menjadi tabel.
5. Tabel yang telah terbentuk dikonversi menjadi bentuk PMML (karena terdapat lebih dari 1 model, konversi yang dilakukan berupa **Ensemble**) menggunakan **Table to PMML Ensemble**.
6. Selanjutnya **PMML** dapat di-compile menggunakan **PMML Compiler**.

## _Evaluation_

![Accuracy](https://github.com/DJahvoe/ETL-menggunakan-KNIME/blob/master/screenshot/accuracy.jpg)<br>
![Scorer](https://github.com/DJahvoe/ETL-menggunakan-KNIME/blob/master/screenshot/scorer.jpg)<br>
Model dievaluasi menggunakan **Entropy Scorer**

## _Deployment_

![Deploy2](https://github.com/DJahvoe/ETL-menggunakan-KNIME/blob/master/screenshot/deploy2.jpg)<br>
Pada tahap deployment digunakan **Predictive Model Markup Language** yang nantinya dapat diterapkan pada sistem menggunakan **Spark Compiled Model Predictor**.
