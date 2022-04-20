# marketing-Campaign
----
- Business Problem <br>
> Terjadi penurunan convertion rate akusisi dalam 3 tahun terakhir. Diperlukan machine learning untuk classification customer potential untuk diakuisisi.

- Business Objectives <br>
> 1.Menargetkan customer potential dan memiliki chance yang besar untuk diakuisisi.<br>
2.Memaksimalkan Profit. <br>
3.Menawarkan Customer product sesuai dengan behaviour customer. <br>

- Model Objectives <br>
> Membangun machine learning yang mampu memprediksi customer potensial dan memiliki chance yang besar untuk di akusisi. <br>

- Model Success Criteria <br>
> Persentase customer yang dapat diprediksi untuk akuisisi minimal 50%. <br>
----

## Feature Groups Provided <br>
![image](https://user-images.githubusercontent.com/88529383/164169342-17fddc02-fb04-4aab-8727-680bfa77cda8.png)
----
## Data Dictionary <br>
![image](https://user-images.githubusercontent.com/88529383/164169499-b2a65071-999a-483c-a001-3142cc8942a5.png)
----

## Definisi Model Dan Baseline Model
- Definisi Model <br>
Classifikasi customer potensial untuk di akuisisi berdasarkan demographics, spend dan engagement.<br>
- Baseline Model <br>
![image](https://user-images.githubusercontent.com/88529383/164232945-e4213569-6e47-45c5-b675-24a6aee493c0.png) <br>
Customer yang diakuisis sebanyak 334 dan customer yang menolak untuk diakuisisi  sebanyak 1906. <br>
----

## Data Cleaning
- Check Missing Value <br>
![image](https://user-images.githubusercontent.com/88529383/164233749-4389964d-b0b4-4762-b187-f5331aa79fd6.png) <br>
Type data untuk tiap kolom telah sesuai, dilihat pada kolom Income terdapat data yang missing dan dihandling dengan menggunakan imputasi median. <br>
- Check Inconsistent Data <br>
![image](https://user-images.githubusercontent.com/88529383/164234343-0f7d7d73-fe27-4740-a124-f6e5242b82ee.png) <br>
pada kolom Marital_Status terdapat beberapa kolom yang memiliki maksud yang sama, jika di analisis lebih lanjut : <br>
1. Jika didefinisikan **Single** adalah kelompok orang yang belum pernah menikah dan tidak memiliki anak, marital status **Absurd** dapat dikategorikan kedalam kelompok **Single**. <br>
2. Jika diperhatikan pada kelompok **Single**,  46% dari populasi memiliki anak kecil dan 40% dari populasi memiliki anak remaja sehigga perlu dipisahkan **Single** memiliki anak menjadi **Divorced**. <br>
3. **Widow**  dan **Alone**  dapat diketegorikan menjadi kelompok **Divorced**. <br>
4. **Together** dapat dikategorikan menjadi **Married**. <br>
5. Tidak terdapat keterangan lanjutan untuk kelompok **YOLO**, karena dari data mereka memiliki anak dan rata rata usia relative muda maka akan dikategorikan menjadi **Married**. <br>
- Check Ouliers <br>
![image](https://user-images.githubusercontent.com/88529383/164235129-17d83d0e-b16c-4849-9bdd-0a27b392b58c.png) <br>
Beberapa kolom numerik memiliki outliers. Outliers dari kolom kolom tersebut akan dihandle menggunakan teknik **capping outliers** <br>
![image](https://user-images.githubusercontent.com/88529383/164235353-ba951dde-9369-4979-ba76-09ae278aa22b.png) <br>
----
## Eksplonatory Data Analysis
----
### Distribusi Data
![image](https://user-images.githubusercontent.com/88529383/164235608-8ab459aa-8c28-4c46-a734-59747517377f.png) <br>
Sebaran data Income dan Age memiliki bentuk yang relatif mirip dengan bentuk **Curve Bell** dapat diasumsikkan bahwa kedua kolom tersebut mengukuti distribu normal. <br>
![image](https://user-images.githubusercontent.com/88529383/164235884-0d53018e-a7db-4da4-9ead-9b45cf8680f5.png) <br>
50,31% dari populasi merupakan customer dengan Pendidikan Graduation. <br>
64.55% dari populasi memiliki marital status Married. <br>

### Analisis
- Chance Customer diakusisi by Tenure <br>
![image](https://user-images.githubusercontent.com/88529383/164236289-ef975b08-83c9-4085-9384-ef727af29bcb.png) <br>
Chance besar untuk di akusisi mengikuti lamanya customer telah bersama supermarket terhitung dari waktu customer mendaftar. <br>
- Chance Customer diakuisis by Education <br>
![image](https://user-images.githubusercontent.com/88529383/164236883-313640c2-8f25-4925-8c13-569cff2909cb.png) <br>
Rata rata income mengikuti tingkat edukasi, semakin tinggi level edukasi maka rata rata income semakin tinggi. Hal ini juga memiliki dampak pada chance customer untuk di akuisisi. Pada grafik barplot terlihat bahwa chance level edukasi PhD memiliki chance yang sangat besar yaitu 21% dan terlihat juga bahwa trend persentase chance untuk diakusisi mengikuti tingkat edukasi. <br>
- Chance Customer diakusisi by Marital Status <br>
![image](https://user-images.githubusercontent.com/88529383/164237219-1ee828d5-e123-4999-adc5-b3e3910e39c3.png) <br>
Dari sisi marital status, status **Single** memiliki chance terbesar untuk diakusisi, persentase chance hingga 39% hampir 3 kali lipat dari chance status **Divorced** dan **Married** untuk di akuisisi. <br>
- Chance Customer diakusisi by Marital Status dan Edukasi <br>
![image](https://user-images.githubusercontent.com/88529383/164237489-6e216e61-a757-4807-b92a-7ec0ef3f361c.png) <br>
Dilihat dari hubungan antara marital status dan edukasi. Chance terbesar untuk diakusisi berada pada kelompok **Single** yang memiliki edukasi **PhD**  dengan persentase chance sebesar 53%. <br>
- Chance Customer diakusisi by Recency <br>
![image](https://user-images.githubusercontent.com/88529383/164237718-e0586e85-ba16-44d2-ad63-d0fac31aa31a.png) <br>
Secara umum, Ketika recency semakin tinggi chance customer untuk diakusisi semakin kecil. <br>
Jika di analisis lebih lanjut dengan melihat hubungan recency dengan marital status, didapatkan beberapa informasi: <br>
> Recency 0-30 hari untuk **single** masih memiliki chance yang besar untuk diakuisisi dan menurun drastis ketika recency diatas 30 hari. <br>
Recency 0-21 hari untuk **Divorced** masih memiliki chance yang besar untuk diakuisis, dan mengalami penurunan drastic Ketika diatas 21 hari. <br>
> untuk **Married** chance yang besar untuk diakuisisi Ketika 0-10 hari dan terus mengalami penurunan chance diakusisi pada recency diatas 10 hari. <br>

Hubungan antara recency dengan edukasi: <br>
> Edukasi **PhD** memiliki chance yang besar pada recency 0-10 hari dan menurun Ketika diatas 10 hari. <br>
 **Master** memiliki chance diakuisisi pada  recency 0-21 hari dan menuru drastis diatas 20 hari. <br>
> **Graduation**  dan **2n Cycle** memiliki chance merunun diatas 10 hari. <br>
- Chance Customer diakusisi By Total Dependents <br>
![image](https://user-images.githubusercontent.com/88529383/164238789-c2e21305-8c49-4b49-a789-b968c83bb125.png) <br>
Jumlah tanggungan memiliki pengaruh terhadap chance customer untuk diakusisi. Chance yang besar Ketika customer tidak memiliki tanggungan sama sekali. <br>
- Monitoring Product Customer Yang Diakuisisi <br>
![image](https://user-images.githubusercontent.com/88529383/164239053-55e1847f-84ff-466d-91c0-8a8e1b89fdb9.png) <br>
Chance customer diakusisi diatas 20% memiliki jumlah pembelian **Gold** diatas 73, **Wines** diatas 504, **Meat** diatas 145, **Fruits** diatas 21, **Sweet** diatas 8,  dan **Fish** diatas 12. <br>
----
## Data Preprocessing
----
<img src = "https://user-images.githubusercontent.com/88529383/164239287-70747d23-a4b7-4b7d-a1d2-eea763451f5f.png" style="display:block; margin:auto;"> </html> 
- Handling Multicolinearity <br>
![image](https://user-images.githubusercontent.com/88529383/164239311-f53a3c0f-1d16-4b15-b3b6-279f3ef776a5.png) <br>
- Ratio Probability Encode <br>
![image](https://user-images.githubusercontent.com/88529383/164239437-350a3b0d-21ee-4e8e-a3d4-3ada25837b36.png) <br>
----
## Modelling
----
![image](https://user-images.githubusercontent.com/88529383/164239602-1265f8ba-d23c-40f2-ab6b-a130507bb69f.png) <br>
model yang dibangun adalah model logistic regression. <br>
- Evaluation Model <br>
![image](https://user-images.githubusercontent.com/88529383/164243538-40c5e5a4-a5ba-4be7-a848-6dc9759c34f9.png) <br>
- Factor Importance <br>
![image](https://user-images.githubusercontent.com/88529383/164243625-327e5d1e-7cc1-430c-acb9-29026f386ad4.png) <br>
----
## Probability Decil Analysis
----
![image](https://user-images.githubusercontent.com/88529383/164243747-49b25e56-38ca-454c-9071-c018f2ef29e5.png) <br>
Dengan mengambil Decil 1 didapatkan percentase akuisisi sebesar 64.2%. <br>

- Audience <br>
![image](https://user-images.githubusercontent.com/88529383/164243915-4026c4c8-6ba5-4d03-8303-4403572d335c.png) <br>
- Prioritas <br>
![image](https://user-images.githubusercontent.com/88529383/164244001-fb8c5dc3-5dc7-43b8-9a4d-bdf8ffd22bbc.png) <br>
Prioritas : <br>
1. High Spend and Low Engagement. <br>
2. Low Spend and High Engagement. <br>
3. High Spend and High Engagement. <br>
4. Low Spend and Low Engagement. <br>
- Treatment- Based On product <br>
prioritas 1 <br>
![image](https://user-images.githubusercontent.com/88529383/164244240-805134ce-6494-4295-9e12-8415a8bfbf5a.png) <br>
prioritas 2 <br>
![image](https://user-images.githubusercontent.com/88529383/164244284-1f84cffe-f748-4450-99a8-7913d1ae2615.png) <br>
prioritas 3 <br>
![image](https://user-images.githubusercontent.com/88529383/164244405-1ec8b148-9009-46b4-8361-0dbe08e5ccca.png) <br>
prioritas 4 <br>
![image](https://user-images.githubusercontent.com/88529383/164244457-f0f66efa-286a-4a17-81f1-e7d77cc6dd4a.png) <br>
----
## Summary
----
1. Terjadi peningkatan untuk mengakuisisi customer potential dengan menggunakan model  peningkatan 4.3 kali lebih tinggi dari baseline model <br>
2. Reduction cost untuk marketing campaign dapat dikurangi hingga 90% <br>







































