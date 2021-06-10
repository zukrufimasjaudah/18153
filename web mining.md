​															**CRAWLING**

*Crawling* adalah sebuah proses di mana mesin pencarian seperti [Google](https://www.wartaekonomi.co.id/tag6696/google) dapat mencari dan memindai konten yang berada di situs web berupa artikel, lembar produk, gambar, link, dll. Mesin pencarian menggunakan alat yang disebut sebagai *crawler* (juga disebut sebagai bot atau spider) untuk memutuskan situs web mana yang akan dipindai.

*Crawler* akan menemukan konten terbaru dengan mengidentifikasi dan merekam setiap link yang ditemukannya pada halaman yang telah dipindai lalu memasukkannya ke dalam daftar URL yang akan di-*crawl*. Tindakan ini sangat penting untuk melakukan strategi SEO karena ini adalah momen ketika mesin pencari menemukan jumlah dan kualitas koneksi pada suatu halaman.

Setiap kali *crawler* mengunjungi halaman situs web, mereka akan melihat melalui "Document Model Object" (atau DOM) pada halaman situs untuk mengetahui apa yang ada di dalamnya. DOM adalah kode HTML dan Javascript yang telah dirender dari halaman situs dan bisa dilihat *crawler* untuk menemukan link ke halaman lain. Ini memungkinkan mesin pencarian untuk menemukan halaman baru di situs web dan setiap link baru tersebut akan dimuat ke dalam antrean yang akan dikunjungi *crawler* di lain waktu.

*Crawling* pada seluruh situs web setiap harinya akan menjadi tugas yang berat sehingga Google biasanya melakukan *crawling* selama beberapa minggu. Proses ini dimulai dengan sekumpulan situs web tepercaya yang berfungsi sebagai dasar untuk mengukur performa situs web lain.

## Cara Kerja Dari Web Crawler

 Secara sederhana, kita bisa umpamakan web crawler sebagai petugas perpustakaan. Mereka awalnya akan mencari copy buku dari percetakan untuk ditaruh di perpustakaan. Hal ini sama seperti crawler yang menjelajah website di internet dan melakukan copy pada page-nya. Page yang di copy akan disimpan dan disortir dalam tumpukan index si web crawler.

Menggunakan alat akses eksternal, kita bisa request informasi yang sudah di sortir tersebut. Biasanya request adalah penggunaan kata kunci dan akses eksternal adalah search engine. Dari sini, web crawler akan menyuguhkan opsi – opsi pilihan website yang sesuai dengan kata kunci yang digunakan.

Selain mengumpulkan copy informasi web, bot crawler juga bisa di-setting untuk keperluan yang lebih khusus. Mulai dari mengumpulkan informasi harga dari platform website e-comerce, analytics website dan masih banyak fungsi lain bisa dipergunakan. Untuk kebutuhan ini, setting dan coding bot hanya perlu dibuat lebih spesifik mengumpulkan informasi tertentu.

## Fungsi Web Crawler

- **Indexing untuk Kebutuhan Search Engine**

- **Analytic Tool**

- **Data Mining**

- **Update Report dan Notifikasi**

  

## Berbagai Masalah dari Web Crawler

- **Menyerap Bandwidth Website**

- **Menyebabkan Masalah Operasi dan Crash**

- **Server Overload**

- **Membuat Security Website Kurang Terjaga**

  

## Crawling Menggunakan Python

Untuk crawling data twitter kita akan menggunakan library [**Tweepy**](https://www.tweepy.org/)**.**

Sebagai contoh kita ingin crawling data twitter dengan kata kunci ***python\*** dengan tweet yang dibuat pada antara tanggal 01 januari 2021 s/d 10 januari 2021 dengan maksimal jumlah tweet adalah 100, kita juga akan *exluced retweet,* sehingga retweet tidak akan di tampilkan. Lalu hasil crawling akan disimpan dengan format .csv

```
import tweepy
import csvaccess_token=""
access_token_secret=""
consumer_key=""
consumer_key_secret=""auth = tweepy.OAuthHandler(consumer_key,consumer_key_secret)
api = tweepy.API(auth)# Open/create a file to append data to
csvFile = open('nama-file.csv', 'w', encoding='utf-8')#Use csv writer
csvWriter = csv.writer(csvFile)for tweet in tweepy.Cursor(api.search, q='#Python -filter:retweets', tweet_mode='extended',lang="id", since='2021-01-01', until='2021-01-10').items(100):
    text = tweet.full_text
    user = tweet.user.name
    created = tweet.created_at
    csvWriter.writerow([created, text.encode('utf-8'), user])
csvWriter = csv.writer(csvFile)
csvFile.close()
```



Referensi :

https://blog.javan.co.id/crawling-data-twitter-menggunakan-python-postman-cffbf14f962c



​												**TEXT PREPROCESSING**



Tahap Text Preprocessing adalah tahapan dimana aplikasi melakukan seleksi data yang akan diproses pada setiap dokumen. Proses preprocessing ini meliputi (1) case folding, (2) tokenizing. (3) filtering, dan (4) stemming.

1. **Case Folding**

Tidak semua dokumen teks konsisten dalam penggunaan huruf kapital. Oleh karena itu, peran Case Folding dibutuhkan dalam mengkonversi keseluruhan teks dalam dokumen menjadi suatu bentuk standar (biasanya huruf kecil atau lowercase).

Sebagai contoh, user yang ingin mendapatkan informasi "KOMPUTER" dan mengetik "KOMPOTER", "KomPUter", atau "komputer", tetap diberikan hasil retrieval yang sama yakni "komputer". Case folding adalah mengubah semua huruf dalam dokumen menjadi huruf kecil. Hanya huruf 'a' sampai dengan 'z' yang diterima. Karakter selain huruf dihilangkan dan dianggap delimiter.

2. **Tokenizing**
Tahap Tokenizing adalah tahap pemotongan string input berdasarkan tiap kata yang menyusunnya. Contoh dari tahap ini dapat dilihat pada gambar dibawah ini. Tokenisasi secara garis besar memecah sekumpulan karakter dalam suatu teks ke dalam satuan kata, bagaimana membedakan karakter karakter tertentu yang dapat diperlakukan sebagai pemisah kata atau bukan.

Sebagai contoh karakter whitespace, seperti enter, tabulasi, spasi dianggap sebagai pemisah kata. Namun untuk karakter petik tunggal (). titik (), semikolon (), titk dua (:) atau lainnya, dapat memiliki peran yang cukup banyak sebagai pemisah kata.



	import nltk
	 
	kalimat = "[MOJOK.co] Manfaat jogging setiap pagi yang pertama adalah meredakan stres. Olahraga itu seperti kode bagi tubuh untuk memproduksi hormon endorfin, agen perangsang rasa bahagia. Dilakukan di pagi hari, ketika udara masih bersih, sejuk, jalanan lengang, gunung terlihat jelas di sebelah utara, manfaat jogging bisa kamu rasakan secara maksimal."
	 
	 
	tokens = nltk.tokenize.word_tokenize(kalimat)
	print(tokens)
	 
	# Hasil
	# ['[', 'MOJOK.co', ']', 'Manfaat', 'jogging', 'setiap', 'pagi', 'yang', 'pertama', 'adalah', 'meredakan', 'stres', '.', 'Olahraga', 'itu', 'seperti', 'kode', 'bagi', 'tubuh', 'untuk', 'memproduksi', 'hormon', 'endorfin', ',', 'agen', 'perangsang', 'rasa', 'bahagia', '.', 'Dilakukan', 'di', 'pagi', 'hari', ',', 'ketika', 'udara', 'masih', 'bersih', ',', 'sejuk', ',', 'jalanan', 'lengang', ',', 'gunung', 'terlihat', 'jelas', 'di', 'sebelah', 'utara', ',', 'manfaat', 'jogging', 'bisa', 'kamu', 'rasakan', 'secara', 'maksimal', '.']
	 
Setelah melalui proses tokenization kita bisa mendapatkan jumlah kemunculan setiap token nya.

3. **Filtering**

Tahap Filtering adalah tahap mengambil kata-kata penting dari hasil token. Bisa menggunakan algoritma stoplist (membuang kata kurang penting) atau wordlist (menyimpan kata penting). Stoplist/stopword adalah kata-kata yang tidak deskriptif yang dapat dibuang dalam pendekatan bag-of-words. Contoh stopwords adalah "yang", "dan", "di", "dari" dan seterusnya. Data stopword akan saya posting dalam artikel berikutnya.

Kata-kata seperti "dari", "yang", "di", dan "ke" adalah beberapa contoh kata-kata yang berfrekuensi tinggi dan dapat ditemukan hampir dalam setiap dokumen (disebut sebagai stopword). Penghilangan stopword ini dapat mengurangi ukuran index dan waktu pemrosesan. Selain itu, juga dapat mengurangi level noise.
Namun terkadang stopping tidak selalu meningkatkan nilai retrieval. Pembangunan daftar stopword (disebut stoplist) yang kurang hati-hati dapat memperburuk kinerja sistem Information Retrieval (IR). Belum ada suatu kesimpulan pasti bahwa penggunaan stopping akan selalu meningkatkan nilai retrieval, karena pada beberapa penelitian, hasil yang didapatkan cenderung bervariasi.

4. **Stemming**

Pembuatan indeks dilakukan karena suatu dokumen tidak dapat dikenali langsung oleh suatu Sistem Temu Kembali Informasi atau Information Retrieval System (IRS). Oleh karena itu. dokumen tersebut terlebih dahulu perlu dipetakan ke dalam suatu representasi dengan menggunakan teks yang berada di dalamnya.

Teknik Stemming diperlukan selain untuk memperkecil jumlah indeks yang berbeda dari suatu dokumen, juga untuk melakukan pengelompokan kata-kata lain yang memiliki kata dasar dan arti yang serupa namun memiliki bentuk atau form yang berbeda karena mendapatkan imbuhan yang berbeda.

Sebagai contoh kata bersama, kebersamaan, menyamai, akan distem ke root word-nya yaitu "sama". Namun, seperti halnya stopping, kinerja stemming juga bervariasi dan sering tergantung pada domain bahasa yang digunakan.

Proses stemming pada teks berbahasa Indonesia berbeda dengan stemming pada teks berbahasa Inggris. Pada teks berbahasa Inggris, proses yang diperlukan hanya proses menghilangkan sufiks. Sedangkan pada teks berbahasa Indonesia semua kata imbuhan baik itu sufiks dan prefiks juga dihilangkan.

Salah satu library yang bisa digunakan dalam melakukan proses stemming bahasa indonesia adalah dengan menggunakan [Library Python Sastrawi](https://github.com/har07/PySastrawi) [1](https://devtrik.com/python/steeming-bahasa-indonesia-python-sastrawi/#easy-footnote-bottom-1-188). Library ini merupakan pengembangan dari [Library PHP Sastrawi](https://github.com/sastrawi/sastrawi) [2](https://devtrik.com/python/steeming-bahasa-indonesia-python-sastrawi/#easy-footnote-bottom-2-188) dimana library tersebut menerapkan algoritma **Algoritma Nazief dan Adriani** [3](https://devtrik.com/python/steeming-bahasa-indonesia-python-sastrawi/#easy-footnote-bottom-3-188). Tahapan algoritma tersebut meliputi :

1. Langkah pertama adalah memeriksa apakah kata tersebut merupakan akar kata (root) terdapat dalam daftar akar kata (root). Kita kata tersebut merupakan akar kata, maka proses dihentikan pada tahap pertama ini.
2. Menghilangkan Inflection Suffixes (“-lah”, “-kah”, “-ku”, “-mu”, atau “-nya”). Jika kata berupa particles (“-lah”, “-kah”, “-tah” atau “-pun”) maka langkah ini diulangi lagi untuk menghapus Possesive Pronouns (“-ku”, “-mu”, atau “-nya”).
3. Menghilangkan derivational suffix (imbuhan turunan). Hilangkan imbuhan -i, -kan, -an.
4. Menghilangkan derivational prefix (awalan turunan). Hilangkan awalan be-, di-, ke-, me-, pe-, se- dan te-.
5. Bila dari langkah 4 di atas belum ketemu juga. Maka lakukan analisis apakah kata tersebut masuk dalam tabel diambiguitas kolom terakhir atau tidak.
6. Bila dari langkah 4 di atas belum ketemu juga. Maka lakukan analisis apakah kata tersebut masuk dalam tabel diambiguitas kolom terakhir atau tidak.
7. Bila semua proses di atas gagal, maka algoritma mengembalikan kata aslinya.

 

## Install Library Python Sastrawi

Instalasi Library ini bisa menggunakan pip dengan perintah pip install Sastrawi .

## Menggunakan Library Python Sastrawi

Setelah library berhasil dipasang, mari kita coba melakukan proses steeming bahasa indonesia dengan meng-import kelas StemmerFactory dari Library Sastrawi

	from Sastrawi.Stemmer.StemmerFactory import StemmerFactory
	factory = StemmerFactory()
	stemmer = factory.create_stemmer()
	 
	kalimat = 'Valentino Rossi tampak sangat menyesal setelah terjatuh pada lap terakhir MotoGP Prancis 2017'
	katadasar = stemmer.stem(kalimat)
	 
	print(katadasar)
	
Referensi:

1. https://id.wikipedia.org/wiki/Penambanganteks

2. https://informatikalogi.com/text-preprocessing/

3. https://devtrik.com/python/steeming-bahasa-indonesia-python-sastrawi/

   ## 						

   ## 					**\*Clustering\***

*Clustering* atau klasterisasi adalah metode pengelompokan data. Menurut Tan, 2006 *clustering* adalah sebuah proses untuk mengelompokan data ke dalam beberapa *cluster* atau kelompok sehingga data dalam satu *cluster* memiliki tingkat kemiripan yang maksimum dan data antar *cluster* memiliki kemiripan yang minimum.

*Clustering* merupakan proses partisi satu *set* objek data ke dalam himpunan bagian yang disebut dengan *cluster.* Objek yang di dalam *cluster* memiliki kemiripan karakteristik antar satu sama lainnya dan berbeda dengan *cluster* yang lain. Partisi tidak dilakukan secara manual melainkan dengan suatu algoritma *clustering*. Oleh karena itu, *clustering* sangat berguna dan bisa menemukan *group* atau kelompokyang tidak dikenal dalam data. *Clustering* banyak digunakan dalam berbagai aplikasi seperti misalnya pada *business inteligence,* pengenalan pola citra*, web search,* bidang ilmu biologi, dan untuk keamanan (*security*). Di dalam *business inteligence*, *clustering* bisa mengatur banyak *customer* ke dalam banyaknya kelompok. Contohnya mengelompokan *customer* ke dalam beberapa *cluster* dengan kesamaan karakteristik yang kuat. *Clustering* juga dikenal sebagai data segmentasi karena *clustering* mempartisi banyak data set ke dalam banyak *group* berdasarkan kesamaannya. Selain itu *clustering* juga bisa sebagai *outlier detection*.

## **Manfaat \*Clustering\***

1. *Clustering* merupakan metode segmentasi data yang sangat berguna dalam prediksi dan analisa masalah bisnis tertentu. Misalnya Segmentasi pasar, marketing dan pemetaan zonasi wilayah.
2. Identifikasi obyek dalam bidang berbagai bidang seperti computer vision dan image processing.

Metode *clustering* juga harus dapat mengukur kemampuannya sendiri dalam usaha untuk menemukan suatu pola tersembunyi pada data yang sedang diteliti. Terdapat berbagai metode yang dapat digunakan untuk mengukur nilai kesamaan antar objek-objek yang dibandingkan. Salah satunya ialah dengan *weighted Euclidean Distance*. Euclidean distance menghitung jarak dua buah point dengan mengetahui nilai dari masing-masing atribut pada kedua poin tersebut. Berikut formula yang digunakan untuk menghitung jarak dengan Euclidean distance:

[![img](https://socs.binus.ac.id/files/2017/03/edy-1.jpg)](https://socs.binus.ac.id/files/2017/03/edy-1.jpg)

Keterangan:
N = Jumlah *record* data
K= Urutan *field* data
r= 2
µk= Bobot *field* yang diberikan *user*

## **Metode \*Clustering\***

### **Hierarchical \*clustering\***

Pada *hierarchical clustering*data dikelompokkan melalui suatu bagan yang berupa hirarki, dimana terdapat penggabungan dua grup yang terdekat disetiap iterasinya ataupun pembagian dari seluruh set data kedalam *cluster.*

[![img](https://socs.binus.ac.id/files/2017/03/edy-3.jpg)](https://socs.binus.ac.id/files/2017/03/edy-3.jpg)Gambar 1.1 Hierarchical Clustering
(Sumber:Han dkk, 2012)

Langkah melakukan *Hierarchical clustering*:

1. Identifikasi *item* dengan jarak terdekat
2. Gabungkan *item* itu kedalam satu *cluster*
3. Hitung jarak antar *cluster*
4. Ulangi dari awal sampai semua terhubung

Contoh metode hierarchy *clustering*: S*ingle Linkage*, *Complete Linkage*, *Average Linkage*, *Average Group Linkage.* 

### **Partitional \*Clustering\***

*Partitional clustering*yaitu data dikelompokkan ke dalam sejumlah *cluster* tanpa adanya struktur hirarki antara satu dengan yang lainnya. Pada metode *partitional clustering*setiap *cluster* memiliki titik pusat *cluster* (centroid) dan secara umum metode ini memiliki fungsi tujuan yaitu meminimumkan jarak (*dissimilarity*) dari seluruh data ke pusat *cluster* masing-masing. Contoh metode partitional *clustering*: K-Means, Fuzzy K-means dan *Mixture Modelling.*

[![img](https://socs.binus.ac.id/files/2017/03/edy-4.jpg)

*K*-Means adalah teknik yang cukup sederhana dan cepat dalam proses *clustering* obyek (*clustering*). Algoritma *K-mean* mendefinisikan *centroid* atau *pusat cluster* dari *cluster* menjadi rata-rata point dari *cluster* tersebut.Dalam penerapan algoritma *k*-Means, jika diberikan sekumpulan data *X* = {x1, x2, …,xn} dimana xi = (xi1, xi2, …, xin) adalah ystem dalam ruang real *Rn*, maka algoritma *k*-Means akan menyusun partisi *X* dalam sejumlah *k cluster* (a priori). Setiap *cluster* memiliki titik tengah (*centroid)* yang merupakan nilai rata rata (*mean)* dari data-data dalam *cluster* tersebut. Tahapan awal, algoritma *k*-Means adalah memilih secara acak *k* buah obyek sebagai *centroid* dalam data. Kemudian, jarak antara obyek dan *centroid* dihitung menggunakan *Euclidian distance*. Algoritma *k*-Means secara *iterative* meningkatkan variasi nilai dalam dalam tiap tiap *cluster* dimana obyek selanjutnya ditempatkan dalam kelompok yang terdekat, dihitung dari titik tengah klaster. Titik tengah baru ditentukan bila semua data telah ditempatkan dalam *cluster* terdekat. Proses penentuan titik tengah dan penempatan data dalam *cluster* diulangi sampai nilai titik tengah dari semua *cluster* yang terbentuk tidak berubah lagi (Han dkk, 2012).

