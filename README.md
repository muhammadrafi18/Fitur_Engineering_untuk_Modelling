# Fitur_Engineering_untuk_Modelling

Feature Engineering adalah proses dimana menerapkan pengetahuan untuk mendapatkan informasi yang lebih dari data. Contohnya dari KTP seseorang, bisa mendapatkan informasi domisili, pembuatan KTP, tanggal lahir, usia, dan jenis kelamin. Menggolongkan orang-orang dengan kategori yang sama untuk membuat machine learning lebih mudah membedakan ciri orang.

## Dataset Titanic

Di pembahasan kali ini saya menggunakan dataset titanic. Dataset ini berasal dari Kaggle, salah satu situs kompetisi machine learning. Dataset ini terdiri dari 2 file, titanic_train.csv dan titanic_test.csv.

## Import library yang digunakan
Import library python biasanya dilakukan di awal sebuah projek. Library yang akan digunakan antara lain:
- pandas untuk proses dataframe dan csv
- matplotlib untuk plotting grafik
- seaborn untuk plotting grafik
- sklearn untuk machine learning model
- string untuk proses string

## Penjelasan dataset
- PassengerId adalah id pada row, maka tidak ada pengaruh terhadap target yang dicari
- Survived adalah target yang akan diprediksi, nilai 0 = Not Survived dan nilai 1 = Survived
- Pclass (Passenger Class) adalah kategori level sosial ekonomi penumpang dengan nilai (1, 2 atau 3):
1. 1 = Upper Class
2. 2 = Middle Class
3. 3 = Lower Class
- Name, Sex dan Age merupakan data self-explanatory
- SibSp adalah jumlah saudara dari penumpang
- Parch adalah jumlah Orang Tua dan anak dari penumpang
- Ticket adalah jumlah tiket penumpang
- Fare adalah tarif yang di kenakan kepada penumpang
- Cabin adalah nomor kabin penumpang
- Embarked adalah pelabuhan pemberangkatan ada 3 pelabuhan (C, Q atau S):
1. C = Cherbourg
2. Q = Queenstown
3. S = Southampton

## Exploring data part 1



Dari plot yang dihasikan dapat terlihat,

ternyata penumpang yang berangkat dari Cherbourg lebih banyak yang selamat, sedangkan penumpang dari Southampton, hanya setengahnya yang selamat.

Untuk orang yang membawa hanya 1 Parent/Children, lebih banyak yang selamat.

Untuk orang dengan Kelas Penumpang 1, kemungkinan selamatnya jauh lebih tinggi.

Dan penumpang dengan Kelas Penumpang 3 hanya sedikit yang selamat.

Dan Orang yang membawa 1 Sibling/Spouse kemungkinan selamatnya jauh lebih besar.

Orang yang membawa 2 Sibling/Spouse kemungkinan selamatnya cukup kecil.

## Exploring data part 2



Untuk Data Fare dan Age, akan membaginya ke dalam beberapa Bin/Group.

Dari fungsi describe sebelumnya, mengetahui bahwa minimal usia yang ada adalah 0.17 tahun dan yang tertua adalah 80 tahun. Sehingga saya rasa membaginya dengan 13 kelompok quantile cukup.

Dan untuk Fare termurah adalah 0 dan termahal adalah 512 (lihat hasil statistik dekriptifnya). Sehingga membaginya dengan 10 kelompok quantile cukup.

Perintah yang pertama bermaksud untuk membagi Fare menjadi 13 bagian dengan fungsi qcut().

Dan perintah yang kedua adalah untuk menggambarkan plot group usia terhadap tingkat keselamatan.

Dapat dilihat bahwa semakin mahal harga tiketnya, semakin besar kemungkinan orang itu selamat, dimulai dari harga 56 ke atas.

Tetapi banyak orang yang selamat dimulai dari 10.5 sudah cukup meningkat, kecuali kejadian yang terjadi pada kelompok pemegang tiket berharga 13-15.742.

Untuk pembagian jumlah bins yang berbeda baik 13 bins untuk "Age" dan 10 bins untuk "Fare" tidak aturan bakunya. 

Tetapi yang diinginkan dari visualisasi berdasarkan pembagian dengan jumlah bins adalah sebaran datanya.

Sebagai contoh untuk "Age" yang memiliki range data 0 (min) s/d 80 (max). Untuk itu, awalnya membagi data menjadi 8 bins katakanlah cukup untuk mereprsentasikan sebaran data. 

Ketika setelah dicek dengan visualisasi sebarannya belum mewakili dan adanya skew. Selanjutnya, menaikkan/menurunkan jumlah bins untuk melihat sebaran data berikut. Untuk "Age" ini terpilihlah 13 bins yang cocok untuk mepresentasikan sebaran data. 

Dengan cara yang sama dapat juga diterapkan untuk "Fare".
Jadi tidak ada aturan baku yang mengatur jumlah bins tersebut.

## Feature Engineering - Part 1



Feature Engineering adalah tentang membuat fitur baru dari fitur yang sudah ada.
Membuat beberapa fitur baru yang bertujuan menaikkan akurasi dari model machine learning kita.

Kategorinya adalah seperti berikut.
- Family Size 1 = Alone
- Family Size 2, 3 dan 4 = Small
- Family Size 5 dan 6 = Medium
- Family Size 7, 8 dan 11 = Large

## Feature Engineering - Part 2

Buat feature baru bernama Ticket_Frequency dengan nilai gabungan dari Ticket yang sama. 



## Feature Engineering - Part 3



Mengelompokkannya menjadi satu pada konten berikutnya

['Miss', 'Mrs','Ms', 'Mlle', 'Lady', 'Mme', 'the Countess', 'Dona'] akan kita ubah menjadi 'Miss/Mrs/Ms'

['Dr', 'Col', 'Major', 'Jonkheer', 'Capt', 'Sir', 'Don', 'Rev'] menjadi 'Dr/Military/Noble/Clergy'

## Kesimpulan


Akurasi yang diperoleh melalui pemodelan tanpa feature engineering adalah 0.81258. Nilai ini lebih rendah 0.02 atau 2% dari pemodelan dengan penggunaan feature engineering.

Ini artinya bahwa penggunaan feature engineering dapat menaikkan akurasi model. 

Karena, fitur turunan (fitur yang direkayasa) melalui teknik feature engineering ini memiliki dampak yang signifikan pada model yang dibangun. Denga kata lain, feature engineering merupakan hal yang terpenting dilakukan untuk meningkatkan performansi model machine learning.
