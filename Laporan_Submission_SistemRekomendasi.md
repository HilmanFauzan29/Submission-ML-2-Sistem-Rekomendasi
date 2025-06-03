# Laporan Proyek Machine Learning Sistem Rekomendasi Musik Spotify - Hilman Fauzan

## Project Overview

Di era digital saat ini, konsumsi musik telah bertransformasi secara drastis dengan munculnya berbagai platform streaming musik yang menawarkan jutaan lagu. Meskipun ketersediaan katalog musik yang masif menjadi keuntungan besar, di sisi lain hal ini juga menciptakan tantangan serius berupa kelebihan informasi bagi pengguna [1]. Pengguna seringkali kesulitan untuk menjelajahi dan menemukan lagu-lagu baru yang sesuai dengan selera mereka di tengah lautan pilihan yang ada. Fenomena ini tidak hanya menghambat pengalaman pengguna dalam menemukan permata tersembunyi, tetapi juga dapat mengurangi tingkat keterlibatan pengguna dengan platform streaming itu sendiri, karena mereka mungkin terjebak dalam mendengarkan lagu yang sama berulang kali atau menyerah mencari hal baru.

Permasalahan kelebihan informasi dalam domain musik ini perlu diselesaikan untuk meningkatkan pengalaman pengguna dan mendorong eksplorasi. Sistem rekomendasi hadir sebagai solusi efektif untuk mengatasi tantangan ini dengan membantu pengguna menemukan item lagu yang relevan dan menarik bagi mereka. Sistem rekomendasi bekerja dengan memprediksi preferensi pengguna terhadap item tertentu atau mengidentifikasi item-item yang kemungkinan besar akan disukai pengguna berdasarkan data yang ada [2].

Berbagai pendekatan sistem rekomendasi telah dikembangkan, termasuk Collaborative Filtering yang berfokus pada perilaku pengguna serupa dan Content-based Filtering yang berfokus pada atribut atau fitur dari item itu sendiri [2]. Mengingat sifat data musik yang kaya akan metadata (genre, artis, album) dan fitur audio yang terukur seperti danceability, energy, tempo, dan acousticness, pendekatan Content-based Filtering sangat relevan dan menjanjikan dalam domain rekomendasi musik. Pendekatan ini bekerja dengan menganalisis karakteristik konten dari lagu-lagu yang disukai pengguna di masa lalu dan kemudian merekomendasikan lagu-lagu lain yang memiliki karakteristik konten yang serupa.

Content-based Filtering merupakan solusi penting untuk mengatasi kelebihan informasi dalam platform musik digital. Pendekatan ini efektif untuk pengguna baru (cold-start), karena dapat memberikan rekomendasi hanya dari beberapa lagu awal yang disukai tanpa memerlukan riwayat interaksi yang panjang. Selain itu, sistem ini mampu merekomendasikan lagu-lagu niche yang memiliki karakteristik unik, serta memberikan alasan yang jelas di balik rekomendasi, sehingga meningkatkan kepercayaan pengguna.

Proyek ini bertujuan membangun sistem rekomendasi musik berbasis Content-based Filtering dengan menganalisis fitur-fitur konten seperti metadata (genre, artis) dan fitur audio (tempo, energy, acousticness). Sistem akan menghitung kemiripan antar lagu untuk menyarankan lagu-lagu yang paling sesuai dengan preferensi pengguna. Penelitian sebelumnya menunjukkan bahwa menggabungkan berbagai jenis fitur konten, baik audio maupun tekstual, dapat meningkatkan kualitas rekomendasi secara signifikan.

### Daftar Pustaka
[1] Wulandari, A. A., Xenora, O. D., & Rahmawati, A. A. (2025). Strategi Digital Marketing untuk Generasi Muda Studi Kasus: Applikasi Spotify di Indonesia. DIGICOM: Jurnal Komunikasi dan Media, 5(1), 9-16.
[2] Anggoro, M. V., & Izzatillah, M. (2022). Sistem Rekomendasi Musik dengan Metode Collaborative Filtering Berbasis Android. STRING (Satuan Tulisan Riset dan Inovasi Teknologi), 7(1), 1-8.

## Business Understanding

### Problem Statements

Dalam konteks platform streaming musik dengan katalog yang masif, beberapa permasalahan utama yang dihadapi pengguna dan ingin diatasi oleh proyek ini adalah:
- Kesulitan dalam Penemuan Musik Baru. Pengguna seringkali kesulitan untuk secara efisien menavigasi jutaan lagu yang tersedia dan menemukan konten musik baru yang relevan dengan selera pribadi mereka.
- Keterbatasan dalam Memanfaatkan Atribut Musik. Pengguna kesulitan untuk secara efektif memanfaatkan atribut dan karakteristik intrinsik lagu (seperti genre, artis, atau fitur audio) sebagai panduan dalam eksplorasi musik.
- Rekomendasi yang Kurang Relevan. Metode penemuan musik yang ada (misalnya, pencarian sederhana atau daftar putar statis) seringkali gagal memberikan rekomendasi lagu yang secara konsisten relevan dengan preferensi spesifik pengguna.
- Kebutuhan Validasi Sistem. Diperlukan metode yang jelas untuk mendemonstrasikan dan memvalidasi bahwa sistem rekomendasi yang dibangun mampu mengidentifikasi dan menyajikan lagu berdasarkan kesamaan konten yang dapat dianalisis.

### Goals

Berdasarkan permasalahan yang diidentifikasi, proyek sistem rekomendasi musik ini menetapkan empat tujuan utama:
- Membangun Sistem Rekomendasi Musik. Mengembangkan dan mengimplementasikan sebuah sistem yang mampu merekomendasikan lagu-lagu baru kepada pengguna dari dataset musik yang tersedia.
- Memanfaatkan Fitur Konten Musik. Menggunakan atribut dan karakteristik intrinsik dari lagu (metadata seperti genre, artis, nama album, dan fitur audio seperti danceability, energy, tempo) sebagai dasar untuk proses rekomendasi.
- Menghasilkan Rekomendasi yang Relevan. Sistem harus mampu menghasilkan daftar rekomendasi lagu yang secara kualitatif dinilai memiliki kemiripan konten yang tinggi dengan lagu input, mencerminkan potensi kecocokan dengan selera pengguna.
- Melakukan Evaluasi Kualitatif. Mendemonstrasikan kinerja sistem rekomendasi melalui studi kasus dengan menampilkan contoh rekomendasi untuk lagu-lagu tertentu dan menganalisis relevansi rekomendasi berdasarkan fitur kontennya.

### Solution statements
- Mengembangkan kode Python menggunakan library seperti pandas, scikit-learn, dan scipy untuk mengimplementasikan alur kerja Content-based Filtering, mulai dari pemuatan data hingga generasi rekomendasi.
- Mengekstraksi, membersihkan, dan memproses fitur-fitur konten yang kaya dari dataset musik, termasuk menerapkan TF-IDF Vectorization pada metadata tekstual (nama lagu, artis, genre, dll.) dan melakukan Standard Scaling pada fitur audio numerik (danceability, energy, tempo, dll.), untuk menciptakan representasi vektor gabungan yang komprehensif untuk setiap lagu.
- Menghitung matriks kemiripan antar semua lagu menggunakan Cosine Similarity pada vektor fitur gabungan yang telah dibuat, dan mengembangkan fungsi rekomendasi yang mampu mengambil lagu input dan mengembalikan daftar lagu-lagu lain yang paling mirip berdasarkan skor kemiripan tertinggi dari matriks tersebut.
- Mendemonstrasikan kinerja sistem rekomendasi dengan memilih beberapa lagu contoh dari dataset, menjalankan fungsi rekomendasi untuk lagu-lagu tersebut, dan menyajikan serta menganalisis output rekomendasi secara kualitatif, menjelaskan bagaimana kesamaan pada atribut konten (teks dan audio) serta skor kemiripan yang tinggi menunjukkan relevansi rekomendasi yang dihasilkan.

## Data Understanding
Pada proyek ini menggunakan dataset high_popularity_spotify_data.csv yang memiliki 29 kolom  1.686 baris dan low_popularity_spotify_data.csv yang memiliki 29 kolom 3.144 baris. Dataset tersebut diambil dari Kaggle. Link dataset tersebut adalah sebagai berikut: https://www.kaggle.com/datasets/solomonameh/spotify-music-dataset/data 

Pada kedua dataset terdapat 29 kolom atau variabel. Variabel-variabel pada dataset high_popularity_spotify_data.csv dan low_popularity_spotify_data.csv adalah sebagai berikut:
- acousticness: Mengukur keyakinan dari 0,0 hingga 1,0 apakah trek tersebut akustik. 1,0 merepresentasikan keyakinan tinggi bahwa trek tersebut akustik.
- danceability: Menggambarkan seberapa cocok sebuah trek untuk menari berdasarkan kombinasi elemen musik termasuk tempo, stabilitas ritme, kekuatan beat, dan keteraturan keseluruhan. Nilai 0,0 paling tidak danceable dan 1,0 paling danceable.
- duration_ms: Durasi trek dalam milidetik.
- energy: Ukuran dari 0,0 hingga 1,0 yang merepresentasikan intensitas dan aktivitas. Trek yang energik terasa cepat, keras, dan bising. 
- instrumentalness: Memprediksi apakah sebuah trek tidak mengandung vokal. Suara "Oooh" dan "Aaah" diperlakukan sebagai instrumental dalam konteks ini. Lagu rap atau spoken word jelas "vokal". Semakin dekat nilai instrumentalness ke 1,0, semakin besar kemungkinan trek tersebut tidak mengandung konten vokal. Nilai di atas 0,5 dimaksudkan untuk merepresentasikan trek instrumental, tetapi keyakinan lebih tinggi saat nilainya mendekati 1,0.
- key: Kunci (key) tempat trek tersebut berada. Bilangan bulat dipetakan ke nada standar menggunakan notasi Pitch Class. E.g. 0 = C, 1 = C♯/D♭, 2 = D, dst. Jika tidak ada kunci yang terdeteksi, nilainya adalah -1.
- liveness: Mendeteksi keberadaan audiens dalam rekaman. Nilai yang lebih tinggi merepresentasikan kemungkinan yang meningkat bahwa trek tersebut direkam secara live. Nilai di atas 0,8 memberikan kemungkinan kuat bahwa trek tersebut live.
- loudness: Tingkat kekerasan keseluruhan trek dalam desibel (dB). Nilai loudness dirata-ratakan di seluruh trek dan paling berguna untuk perbandingan relatif kekerasan trek. Nilai khas berkisar antara -60 hingga 0 db.
- mode: Menunjukkan modalitas (mayor atau minor) dari sebuah komposisi, ditentukan oleh urutan interval dalam skalanya. Mayor direpresentasikan oleh 1 dan minor adalah 0.
- speechiness: Mendeteksi keberadaan elemen ucapan dalam sebuah trek. Semakin murni ucapan (misalnya, podcast, buku audio, puisi), semakin dekat nilainya ke 1,0. Nilai di atas 0,66 kemungkinan besar adalah trek yang hanya terdiri dari ucapan. Nilai antara 0,33 dan 0,66 mungkin berisi musik dan ucapan, baik dalam bagian atau layer, termasuk kasus seperti musik rap. Nilai di bawah 0,33 kemungkinan besar adalah musik dan konten non-ucapan lainnya.
- tempo: Perkiraan tempo keseluruhan trek dalam beats per minute (BPM). Dalam terminologi musik, tempo adalah kecepatan atau laju ritme tertentu.
- time_signature: Perkiraan tanda birama (time signature) keseluruhan trek. Tanda birama (meter) adalah konvensi notasi untuk menentukan berapa banyak ketukan yang ada dalam setiap measure (birama). Tanda birama bernilai integer.
- valence: Ukuran dari 0,0 hingga 1,0 yang menggambarkan kepositifan musik yang disampaikan oleh sebuah trek. Trek dengan valence tinggi terdengar lebih positif (misalnya, ceria, gembira, euforia), sementara trek dengan valence rendah terdengar lebih negatif (misalnya, sedih, depresi, marah).
- track_artist: Nama artis utama atau artis yang ditampilkan dalam trek.
- track_album_name: Nama album tempat trek tersebut berada.
- track_name: Nama trek atau lagu itu sendiri.
- playlist_name: Nama playlist tempat trek tersebut ditemukan dalam dataset.
- playlist_genre: Genre utama playlist tempat trek tersebut ditemukan, misalnya pop, rock, dan jazz.
- playlist_subgenre: Subgenre spesifik dari playlist tempat trek tersebut ditemukan , misalnya mainstream pop, classic rock, dan smooth jazz.
- track_album_release_date: Tanggal rilis album. Memberikan konteks waktu.
- track_id: ID unik Spotify untuk trek tersebut.
- id: Kolom ID lain yang mungkin ada dalam dataset.
- track_album_id: ID unik Spotify untuk album tempat trek tersebut berada.
- playlist_id: ID unik untuk playlist tempat trek tersebut ditemukan.
- track_href: URL ke endpoint Web API lengkap untuk mendapatkan data trek.
- uri: Spotify URI (Uniform Resource Identifier) untuk trek tersebut.
- analysis_url: URL ke endpoint Web API yang berisi data analisis audio yang lebih detail untuk trek tersebut.
- type: Tipe objek Spotify, dalam kasus ini biasanya 'track'.
- track_popularity: Angka dari 0 hingga 100 yang merupakan ukuran popularitas trek. Angka ini sebagian besar didasarkan pada jumlah pemutaran trek baru-baru ini dan seberapa sering trek tersebut diputar dibandingkan dengan trek lainnya. Catatan: Popularitas ini bisa berubah seiring waktu.
- Popularity: Kolom lain yang mungkin merepresentasikan popularitas

Pada data understanding, dilakukan juga pengecekan kondisi dari kedua dataset. Kondisi dataset yang dicek yaitu missing value dan data/baris duplikat. Kondisi dari dataset yaitu sebagai berikut.
- Missing Value. Kondisi pada dataset high_popularity_spotify_data.csv, ditemukan bahwa hanya terdapat 1 missing value pada kolom track_album_name saja. Sedangkan pada dataset low_popularity_spotify_data.csv, ditemukan 1 dalam kolom time_signature, 1 dalam kolom speechiness, 1 dalam kolom danceability, 1 dalam kolom duration_ms, 1 dalam kolom energy, 1 dalam kolom id, 1 dalam kolom track_href, 1 dalam kolom mode, 1 dalam kolom uri, 1 dalam kolom type, 1 dalam kolom analysis_url, 1 dalam kolom instrumentalness, 1 dalam kolom valenve, 1 dalam kolom key, 1 dalam kolom tempo, 1 dalam kolom loudnesss, 1 dalam kolom acousticness, dan 1 dalam kolom liveness.
- Baris Duplikat. Pada kedua dataset high_popularity_spotify_data.csv dan low_popularity_spotify_data.csv tidak memiliki baris atau data duplikat.

Lalu dilakukan visualisasi pada Distribusi Fitur Numerik, distribusi jumlah lagu pada playlist genre, ditribusi jumlah lagu pada playlist subgenre, dan Distribusi Artis Teratas. Penjelasannya diuraikan pada Data Preparation.

## Data Preparation
Pada bagian data preparation, tahapan yang dilakukan yaitu sebagai berikut:
- Penanganan missing value pada high_popularity_spotify_data.csv yang dilakukan pada kolom track_album_name dengan mengisi missing value tersebut. 
- Penanganan missing value pada low_popularity_spotify_data.csv yang dilakukan pada kolom yang disebutkan dalam data understanding di atas. 
- Dilakukan penggabungan kedua data set yang digabung dalam fungsi df_combined. Data gabungan ini memiliki 29 kolom dan 4.831 baris. Lalu menggunakan df_combined sebagai variabel utama "df" yang akan digunakan dalam persiapan data selanjutnya. 
- Melakukan pengecekan dataset gabungan. Pertama melihat 5 baris pertama dari dataset gabungan.
- Melihat informasi umum dataset untuk melihat kondisi dan tipe data dari setiap kolom. 
- Mengecek missing value pada data gabungan. Pada data gabungan tidak terdapat missing value.
- Mengecek baris duplikat, pada data gabungan terdapat 43 baris duplikat yang harus ditangani.
- Penanganan baris duplikat pada data gabungan dengan menghapus 43 baris tersebut karena tidak akan mempengaruhi jumlah baris, sebab jumlah dataset sangat banyak. Data gabungan setelah penanganan baris duplikat sebanyak 4.788.
- Melihat informasi Statistik deskriptif untuk kolom numerik pada DataFrame gabungan.
- Melihat dan mengecek nilai unik pada kolom kategorikal penting. Hasil pengecekan data unik pada kolom kategorikal dimana terdapat 35 pada kolom playlist_genre, 84 pada kolom playlist_subgenre, dan 3.390 pada kolom track_artist. Contoh data unik pada kolom playlist_genre yaitu 'pop' 'rock' 'jazz' 'classical' 'hip-hop' 'afrobeats' 'latin' 'indian' 'country' 'r&b'. Contoh data unik pada kolom playlist_subgenre yaitu 'mainstream' 'classic' 'essential' 'modern' 'gangster' 'trap' 'nigerian' 'hip-hop' 'bollywood' 'indie'. Contoh data unik pada kolom track_artist yaitu 'Lady Gaga, Bruno Mars' 'Billie Eilish' 'Gracie Abrams' 'Sabrina Carpenter' 'ROSÉ, Bruno Mars' 'Chappell Roan' 'Addison Rae' 'Gigi Perez' 'The Weeknd, Playboi Carti' 'Charli xcx, Billie Eilish'.
- Memvisualisasikan data gabungan. Beberapa visualisasi yang dilakukan yaitu distribusi frekuensi pada danceability, energy, valence, tempo, loudness, acousticness, instrumentalness, liveness, speechiness, duration_ms, dan track_popularity. Lalu distribusi jumlah lagu pada playlist genre dan playlist subgenre. Terakhir grafik 20 artis teratas berdasarkan jumlah lagu.
- Membuat kombinasi fitur tekstual dengan mengumpulkan informasi dari kolom-kolom seperti nama lagu, artis, album, serta genre dan subgenre playlist ke dalam satu kolom baru bernama 'text_features'. Proses ini dimulai dengan mengidentifikasi kolom-kolom tekstual yang benar-benar ada dalam DataFrame, memastikan datanya bertipe string dan mengisi nilai yang hilang dengan string kosong untuk mencegah error, lalu menggabungkan teks dari kolom-kolom yang sudah disiapkan tersebut untuk setiap lagu menjadi satu string panjang di kolom 'text_features', yang hasilnya sangat penting sebagai representasi konten tekstual setiap item dan siap digunakan untuk ekstraksi fitur teks lebih lanjut seperti TF-IDF dalam sistem rekomendasi berbasis konten.
- Penggunaan TF-IDF Vectorizer untuk mengubah fitur tekstual gabungan dari kolom 'text_features' menjadi representasi numerik. Ini dilakukan dengan menginisialisasi TfidfVectorizer dari scikit-learn yang dikonfigurasi untuk mengabaikan kata-kata umum dalam bahasa Inggris (stopwords) dan membatasi jumlah fitur (kata unik) hingga max_features tertentu (dalam contoh ini 10000), kemudian memproses teks dari setiap lagu untuk menghasilkan matriks tfidf_matrix. Matriks sparse ini secara efisien merepresentasikan pentingnya setiap kata dalam konteks setiap lagu dan seluruh dataset, menjadikannya komponen penting dari vektor konten yang siap untuk perhitungan kemiripan, dengan tambahan pengecekan untuk menangani kasus jika kolom teks gabungan ternyata kosong.
- Memilih fitur numerik yang bertujuan untuk secara otomatis mengidentifikasi dan mengisolasi semua fitur-fitur yang memiliki tipe data numerik (yang mencakup fitur audio, popularitas, dll.) dari DataFrame utama df. Ini dilakukan dengan menggunakan metode df.select_dtypes(include=np.number) yang secara efisien memilih kolom-kolom berbasis angka, menyimpan nama-nama kolom yang ditemukan dalam daftar numeric_cols_exist, dan kemudian membuat sebuah DataFrame baru bernama numeric_data yang hanya berisi data dari kolom-kolom numerik terpilih tersebut, menjadikannya siap untuk langkah pemrosesan selanjutnya seperti penskalaan yang krusial dalam pembentukan vektor fitur konten untuk perhitungan kemiripan.
- Menskalakan fitur numerik menggunakan StandardScaler dari scikit-learn.
- Menggabungkan Fitur Tekstual (TF-IDF) dan Numerik (Scaled) menggunakan scipy.sparse.hstack, menumpuknya secara horizontal untuk membentuk vektor fitur gabungan tunggal per lagu bernama combined_features, setelah terlebih dahulu memastikan bahwa kedua matriks memiliki jumlah baris (jumlah lagu) yang sama, yang mana hasil gabungan ini merupakan representasi konten akhir setiap lagu yang akan digunakan untuk menghitung kemiripan antar item.
- Menyimpan ID lagu yang berfungsi untuk secara otomatis memilih atau membuat kolom identifikasi unik (ID) untuk setiap lagu dalam DataFrame, yang krusial untuk menghubungkan hasil perhitungan kemiripan (berdasarkan index numerik) kembali ke informasi lagu yang relevan. Proses ini secara berurutan memeriksa apakah kolom 'track_id' atau 'id' tersedia dan lengkap untuk dijadikan basis ID; jika tidak ada yang cocok, akan membuat kolom ID baru 'generated_id' berdasarkan index DataFrame; pada akhirnya, nama kolom ID yang dipilih atau dibuat disimpan dalam variabel id_col, memastikan setiap lagu memiliki pengenal yang handal untuk keperluan mapping dan lookup rekomendasi.
- Membuat ID internal unik dan hashable er lagu dengan menggabungkan index DataFrame dan ID basis yang dipilih (id_col) menjadi kolom baru 'song_id_internal', lalu mengubah kolom ini menjadi daftar song_ids, memastikan setiap lagu memiliki pengenal tunggal yang pasti unik dan siap digunakan untuk pembuatan mapping index ke fitur gabungan.
- Membuat mapping dari ID lagu ke index dalam matriks fitur. Tahap data preparation diselesaikan dengan membuat mapping antara ID internal unik setiap lagu (song_ids) dan index numerik (posisi) mereka dalam matriks fitur gabungan serta matriks kemiripan. Dua kamus, id_to_index yang memetakan ID ke index dan index_to_id yang memetakan index kembali ke ID lagu, dibuat menggunakan list song_ids. Mappings ini sangat penting karena matriks-matriks tersebut diakses menggunakan index numerik, sehingga mapping ini menjembatani ID lagu yang mudah dikenali dengan lokasi data yang sebenarnya, memungkinkan sistem rekomendasi untuk mencari dan mengidentifikasi lagu dengan efisien.

## Modeling
Model yang dibangun dalam proyek ini menggunakan pendekatan Content-based Filtering. Model Content-based Filtering bekerja dengan menganalisis atribut atau fitur intrinsik dari item (dalam hal ini, lagu) untuk merekomendasikan item lain yang memiliki karakteristik serupa. Fokus utama dari model ini adalah pada konten dari lagu itu sendiri, bukan pada interaksi atau perilaku pengguna lain.

Proses pembangunan model dan generasi rekomendasi dalam proyek ini melibatkan beberapa langkah kunci, seperti yang diimplementasikan dalam kode:
1. Representasi Fitur Konten:
   - Setiap lagu direpresentasikan sebagai vektor numerik yang komprehensif.
   - Representasi ini menggabungkan dua jenis fitur utama yang diekstraksi dari dataset, yaitu Fitur Tekstual/Kategorikal (Metadata seperti nama lagu, artis, album, genre playlist, dan subgenre digabungkan menjadi satu string teks per lagu. String ini kemudian diubah menjadi representasi numerik menggunakan TF-IDF Vectorization. TF-IDF memberikan bobot pada kata-kata berdasarkan frekuensinya dalam lagu dan jarang munculnya di seluruh dataset, menangkap pentingnya istilah-istilah dalam mendeskripsikan konten tekstual lagu) dan Fitur Numerik (Atribut audio yang terukur seperti danceability, energy, tempo, loudness, acousticness, instrumentalness, liveness, valence, duration_ms, key, mode, dan time_signature digunakan sebagai fitur numerik. Fitur-fitur ini diskalakan menggunakan StandardScaler untuk memastikan bahwa rentang nilai yang berbeda tidak secara tidak proporsional memengaruhi perhitungan kemiripan).
   - Matriks output dari TF-IDF Vectorizer (matriks sparse) dan matriks output dari StandardScaler (matriks dense) kemudian digabungkan secara horizontal menggunakan scipy.sparse.hstack untuk membentuk satu matriks fitur gabungan (combined_features) yang merepresentasikan konten setiap lagu.
2. Perhitungan Matriks Kemiripan:
   - Setelah representasi fitur gabungan untuk semua lagu dibuat, langkah selanjutnya adalah menghitung seberapa mirip setiap lagu dengan setiap lagu lainnya.
   - Metrik Cosine Similarity digunakan untuk mengukur kemiripan antara vektor fitur gabungan dari setiap pasangan lagu. Cosine Similarity mengukur kosinus sudut antara dua vektor; nilai yang mendekati 1 menunjukkan kemiripan tinggi, sementara nilai yang mendekati 0 menunjukkan kemiripan rendah.
   - Hasil perhitungan ini adalah similarity_matrix, sebuah matriks persegi di mana setiap elemen (i, j) merepresentasikan skor kemiripan antara lagu ke-i dan lagu ke-j dalam dataset. Matriks ini secara efektif adalah 'model' yang menyimpan hubungan kemiripan berbasis konten antar semua item.
3. Generasi Rekomendasi:
   - Proses rekomendasi dilakukan menggunakan fungsi get_content_based_recommendations.
   - Ketika fungsi ini dipanggil dengan ID lagu input, ia akan mencari index lagu tersebut dalam similarity_matrix.
   - Baris yang sesuai dengan index lagu input diambil dari similarity_matrix, yang berisi skor kemiripan lagu input dengan semua lagu lain dalam dataset.
   - Skor-skor ini kemudian diurutkan secara menurun.
   - Top-N lagu dengan skor kemiripan tertinggi (tidak termasuk lagu input itu sendiri) dipilih sebagai rekomendasi.
   - Informasi detail dari lagu-lagu rekomendasi ini diambil dari DataFrame asli dan disajikan bersama skor kemiripan mereka.

Output dari model ini adalah daftar Top-N Recommendation. Berikut adalah contoh output yang dihasilkan oleh sistem untuk lagu input 'Tranquillo' oleh Escix V:
Rekomendasi untuk Lagu Input (Index: 3591)
| Keterangan         | Nilai                                                                 |
|--------------------|-----------------------------------------------------------------------|
| **ID Internal**    | `3591_7A1uziu96JlZBqgbYnx3VE`                                         |
| **Track Name**     | *Tranquillo*                                                          |
| **Track Artist**   | Escix V                                                               |
| **Playlist Genre** | wellness                                                              |
| **Subgenre**       | yoga                                                                  |
| **Fitur Audio**    | Danceability = 0.15  <br> Energy = 0.01 <br> Tempo = 136.38 <br> Loudness = -37.56 |

Rekomendasi (Top 5):
| song_id_internal | track_name | track_artist | playlist_genre | playlist_subgenre | Similarity_Score |
| :----------------- | :--------- | :----------- | :------------- | :---------------- | :--------------- |
| 3624_4jS79eUku1DjatFHoM06Xd | Sanyog | Aasmi Jayavant | wellness | yoga | 0.979203 |
| 3489_4TGVSsk5tV5rPA2eZ5QW2s | Echoes | Leya Watson | ambient | chill | 0.957565 |
| 3555_4a20vranOH3ic2txQ463jc | Desear | Julia Alvarez | wellness | yoga | 0.949875 |
| 3530_4OgLtqCE1dMYnEdcgZ0ZSS | Timeless | Elm Lake | ambient | chill | 0.926934 |
| 3588_6uSzJ1maVPTAkGS9YdLIQy | Aspiration | Silent Motions | wellness | yoga | 0.925059 |

Kelebihan dan kekurangan Content-based Filtering:
1. Kelebihan:
   - Mengatasi Cold-Start Pengguna Baru. Sistem dapat merekomendasikan item kepada pengguna baru tanpa memerlukan data interaksi historis mereka, cukup dengan mengetahui preferensi awal (misalnya, satu atau dua lagu yang mereka sukai).
   - Rekomendasi Item Niche. Mampu merekomendasikan item yang kurang populer jika kontennya mirip dengan item yang disukai pengguna, tidak hanya terpaku pada item populer seperti Collaborative Filtering sederhana.
   - Penjelasan Rekomendasi. Rekomendasi seringkali lebih mudah dijelaskan kepada pengguna ("Anda mungkin menyukai ini karena mirip dengan X"), karena didasarkan pada atribut item yang dapat dipahami.
   - Tidak Memerlukan Data Pengguna Lain. Model dibangun hanya berdasarkan data item, tidak memerlukan data interaksi dari banyak pengguna lain.

2. Kekurangan:
   - Kelebihan Konten (Content Over-specialization). Sistem cenderung hanya merekomendasikan item yang sangat mirip dengan item yang sudah disukai pengguna, membatasi penemuan item yang benar-benar baru atau di luar "gelembung" preferensi pengguna. Pengguna mungkin tidak akan pernah direkomendasikan genre atau artis yang sama sekali berbeda dari yang sudah mereka kenal.
   - Membutuhkan Data Konten yang Kaya. Kualitas rekomendasi sangat bergantung pada seberapa kaya, deskriptif, dan terstruktur data konten item yang tersedia. Jika data konten buruk atau tidak lengkap, model tidak akan bekerja dengan baik.
   - Tidak Mempertimbangkan Perilaku Pengguna Lain. Model tidak dapat memanfaatkan pola atau tren selera kolektif dari komunitas pengguna, yang seringkali dapat mengarah pada rekomendasi yang menarik dan tak terduga.

Meskipun proyek ini fokus pada Content-based Filtering, penting untuk mengidentifikasi alternatif solusi yang relevan:
1. Collaborative Filtering. Pendekatan ini bisa menjadi alternatif jika data interaksi pengguna (seperti riwayat mendengarkan atau rating) tersedia. Kelebihannya adalah mampu menangkap pola selera dari komunitas dan merekomendasikan item yang disukai oleh pengguna serupa, bahkan jika konten item tersebut tidak secara langsung mirip dengan item yang sudah disukai pengguna. Kekurangannya adalah masalah cold-start untuk pengguna atau item baru dan ketergantungan pada data interaksi yang cukup.
2. Hybrid Approach. Menggabungkan Content-based dan Collaborative Filtering dapat menjadi solusi yang lebih kuat, memanfaatkan kelebihan keduanya (misalnya, menggunakan Content-based untuk cold-start dan item niche, serta Collaborative Filtering untuk menangkap tren komunitas). Implementasi ini akan lebih kompleks tetapi berpotensi memberikan rekomendasi yang lebih akurat dan beragam.

Dalam submission ini, Content-based Filtering dipilih sebagai pendekatan utama karena ketersediaan data konten yang kaya dan relevansinya dalam mengatasi masalah cold-start dan rekomendasi berbasis atribut item musik.

## Evaluation
Tahap evaluasi ini bertujuan untuk mengukur dan mendemonstrasikan kinerja sistem rekomendasi musik yang telah dibangun dalam mencapai tujuan proyek, khususnya dalam menghasilkan rekomendasi yang relevan berdasarkan konten dan memvalidasi kemampuan sistem.

Mengingat pendekatan yang diimplementasikan adalah Content-based Filtering murni dan ketersediaan data dalam proyek ini (dataset statis tanpa data interaksi pengguna eksplisit seperti rating atau riwayat mendengarkan), metrik evaluasi kuantitatif standar seperti Root Mean Squared Error (RMSE) untuk prediksi rating atau metrik peringkat seperti Recall@K dan NDCG yang membutuhkan data ground truth interaksi pengguna tidak dapat diterapkan secara langsung. Namun, untuk memberikan gambaran kuantitatif mengenai kinerja sistem, metrik Precision@K dapat diimplementasikan dengan menggunakan playlist_genre atau playlist_subgenre sebagai ground truth (proxy relevansi). Selain itu, metrik evaluasi yang paling sesuai dan relevan untuk proyek ini adalah Evaluasi Kualitatif Berbasis Konten (Qualitative Content-Based Evaluation) melalui demonstrasi sistem, yang fokus pada analisis mengapa rekomendasi yang dihasilkan relevan dengan lagu input berdasarkan kesamaan atribut konten item.

Cara kerja dari metrik evaluasi kualitatif yaitu sebagai berikut:
- Memilih sejumlah lagu contoh dari dataset yang merepresentasikan keragaman konten (genre, karakteristik audio, popularitas).
- Menjalankan sistem rekomendasi (fungsi get_content_based_recommendations) untuk setiap lagu contoh tersebut guna mendapatkan daftar Top-N lagu rekomendasi.
- Menganalisis secara deskriptif output rekomendasi untuk setiap lagu contoh. Analisis ini meliputi memeriksa kesamaan pada metadata tekstual (genre, subgenre, artis, nama) antara lagu input dan lagu-lagu yang direkomendasikan. Lalu mempertimbangkan kesamaan pada fitur audio (danceability, energy, tempo, loudness, dll.) antara lagu input dan lagu-lagu rekomendasi. Terakhir menganalisis nilai Similarity Score (Cosine Similarity) yang dihasilkan oleh model untuk setiap rekomendasi. Skor yang tinggi mengindikasikan bahwa model menganggap lagu tersebut sangat mirip dengan lagu input di ruang fitur konten.
- Menyajikan temuan dari analisis ini sebagai bukti bahwa sistem berhasil mengidentifikasi dan merekomendasikan lagu berdasarkan kesamaan konten, yang secara implisit menunjukkan relevansi rekomendasi dalam konteks Content-based Filtering.

Metrik ini secara langsung selaras dengan Goals proyek untuk "Menghasilkan Rekomendasi yang Relevan" (dalam konteks kemiripan konten) dan "Melakukan Evaluasi Kualitatif".

Berdasarkan evaluasi kualitatif melalui demonstrasi sistem pada beberapa lagu contoh, hasil proyek menunjukkan bahwa sistem rekomendasi musik berbasis Content-based Filtering yang dibangun berhasil mengidentifikasi dan menyajikan lagu-lagu yang memiliki kemiripan konten yang tinggi dengan lagu input. Sebagai contoh, demonstrasi untuk lagu input 'Tranquillo' oleh Escix V (Genre: wellness, Subgenre: yoga, dengan fitur audio seperti Danceability 0.15, Energy 0.01, Loudness -37.56) menghasilkan rekomendasi Top 5 seperti pada Top-N Recomendation yang diuraikan pada Modelling. Analisis hasil tersebut menunjukkan:
- Relevansi Berdasarkan Metadata. Rekomendasi didominasi oleh lagu-lagu dari genre 'wellness' dan 'ambient' dengan subgenre terkait seperti 'yoga' dan 'chill'. Ini secara langsung mencerminkan genre dan subgenre dari lagu input, menunjukkan bahwa sistem berhasil menangkap kemiripan berdasarkan metadata tekstual/kategorikal.
- Relevansi Berdasarkan Fitur Audio & Skor Kemiripan. Lagu-lagu rekomendasi memiliki skor kemiripan (Similarity Score) yang sangat tinggi, berkisar antara 0.925 hingga 0.979. Skor tinggi ini mengindikasikan bahwa model menganggap lagu-lagu tersebut sangat dekat dengan lagu input di ruang fitur gabungan, yang mencakup fitur audio yang diskalakan. Lagu input 'Tranquillo' memiliki karakteristik audio yang sangat spesifik (misalnya, energi dan loudness yang sangat rendah, danceability rendah). Skor kemiripan yang tinggi untuk lagu-lagu rekomendasi menunjukkan bahwa lagu-lagu tersebut kemungkinan besar memiliki pola fitur audio yang serupa, yang berkontribusi signifikan pada kemiripan konten yang diukur.
- Penemuan Item Serupa. Sistem berhasil menemukan lagu-lagu yang memiliki "rasa" atau karakteristik yang mirip dengan lagu input, meskipun mungkin dari artis yang berbeda, yang merupakan tujuan utama dari Content-based Filtering.

Selanjutnya evaluasi menggunakan metrik Precision@K. Dalam evaluasi sistem rekomendasi, Precision@K adalah metrik yang digunakan untuk mengukur seberapa akurat daftar rekomendasi Top-N (di mana N adalah K) yang diberikan oleh sistem. Metrik ini berfokus pada proporsi item yang relevan di antara K item teratas yang direkomendasikan. Cara kerja metrik Precision@K yaitu sebagai berikut:
- K adalah angka yang menentukan berapa banyak item teratas dalam daftar rekomendasi yang akan dievaluasi. Misalnya, jika K=5, kita hanya akan melihat 5 rekomendasi teratas.
- Untuk setiap rekomendasi di dalam Top K, kita perlu menentukan apakah item tersebut "relevan" atau tidak. Definisi "relevan" ini sangat krusial dan harus ditetapkan di awal.
- Setelah mengidentifikasi item-item yang relevan di antara Top K rekomendasi, Precision@K dihitung menggunakan formula berikut:
$$
Precision@K = \frac{\text{Jumlah item relevan dalam Top } K}{K}
$$ 

Dalam proyek sistem rekomendasi musik berbasis Content-based Filtering ini, dimana data interaksi pengguna eksplisit tidak tersedia, Precision@K diadaptasi dengan menggunakan playlist_genre atau playlist_subgenre sebagai ground truth (indikator relevansi).
Proses Penggunaan pada Proyek ini yaitu sebagai berikut:
- Penentuan K. Pada proyek telah memilih K=5 untuk demonstrasi Top 5 rekomendasi.
- Definisi Relevansi di Proyek. Sebuah lagu rekomendasi dianggap "relevan" jika playlist_genre (atau playlist_subgenre, tergantung pilihan yang lebih spesifik) dari lagu rekomendasi tersebut sama persis dengan playlist_genre (atau playlist_subgenre) dari lagu input yang menjadi dasar rekomendasi. Ini adalah asumsi yang masuk akal untuk sistem Content-based, karena jika lagu-lagu memiliki genre yang sama, mereka cenderung memiliki karakteristik konten yang serupa.
- Perhitungan, disini akan menghitung untuk lagu "Die With A Smile". Lagu input yaitu "Die With A Smile" dengan Playlist Genre "pop" dan Playlist Subgenre "mainstream". Sistem berhasil mendapatkan 5 rekomendasi teratas, lalu memeriksa relevansi berdasarkna Genre "pop" :
 - Rekomendasi 1: 'Die With A Smile' (versi lain) - Genre: 'gaming' (Tidak Relevan)
 - Rekomendasi 2: 'Die With A Smile' (versi lain) - Genre: 'pop' (Relevan)
 - Rekomendasi 3: 'Iris' - Genre: 'pop' (Relevan)
 - Rekomendasi 4: 'Iris' - Genre: 'pop' (Relevan)
 - Rekomendasi 5: 'Iris' - Genre: 'rock' (Tidak Relevan)
Lalu menghitung nilai Precision@k dengan rumus yang tadi sudah dituliskan dengan nilai k=5.
$$
\text{Precision@5} = \frac{3}{5} = 0.60 = 60\%
$$

Ini berarti 60% dari 5 rekomendasi teratas memiliki genre yang sama dengan lagu input.

Dengan demikian, evaluasi ini secara efektif mendemonstrasikan bahwa sistem rekomendasi berbasis Content-based Filtering yang dibangun berhasil memanfaatkan fitur-fitur konten yang kaya dari dataset untuk mengidentifikasi dan merekomendasikan lagu-lagu yang relevan berdasarkan kemiripan konten. Hal ini didukung oleh kombinasi metrik:
- Evaluasi Kualitatif Berbasis Konten. Melalui analisis deskriptif pada contoh rekomendasi, sistem terbukti mampu menyajikan lagu-lagu dengan kesamaan yang jelas pada metadata (genre, subgenre) dan karakteristik fitur audio dengan lagu input, didukung oleh skor kemiripan (Cosine Similarity) yang tinggi.
- Precision@K. Hasil Precision@K menunjukkan 60% relevansi berdasarkan kesamaan genre pada contoh kasus, memberikan gambaran kuantitatif tambahan mengenai presisi sistem dalam merekomendasikan lagu-lagu dengan atribut konten yang konsisten.

Kedua metrik ini secara kolektif menegaskan bahwa tujuan proyek telah tercapai, yaitu menghasilkan rekomendasi yang relevan dan dapat dievaluasi berdasarkan konten.

Selanjutnya hasil evaluasi sistem rekomendasi musik berbasis Content-based Filtering yang telah dibangun dan diimplementasikan dalam proyek ini secara langsung menjawab permasalahan yang diidentifikasi, mencapai tujuan yang ditetapkan, dan mewujudkan solusi yang diusulkan.
1. Problem Statements
   - Kesulitan dalam Penemuan Musik Baru & Keterbatasan dalam Memanfaatkan Atribut Musik. Sistem ini mengatasi kelebihan informasi dan kesulitan penemuan dengan menyediakan mekanisme terstruktur untuk menganalisis dan memanfaatkan atribut intrinsik lagu (metadata tekstual dan fitur audio). Pengguna tidak lagi harus secara manual menelusuri katalog besar; sistem yang akan memproses konten lagu dan menemukan item yang relevan secara otomatis.
   - Rekomendasi yang Kurang Relevan. Dengan mendasarkan rekomendasi pada kemiripan konten yang terukur (melalui Cosine Similarity pada vektor fitur gabungan), sistem ini secara inheren bertujuan untuk memberikan rekomendasi yang lebih relevan dengan selera pengguna yang ditunjukkan oleh lagu input, karena rekomendasi tersebut memiliki karakteristik konten yang serupa.
   - Kebutuhan Validasi Sistem. Proyek ini secara eksplisit menyertakan tahap evaluasi kualitatif yang mendemonstrasikan cara kerja sistem dan relevansi rekomendasinya berdasarkan analisis kesamaan konten dan skor kemiripan, sehingga memvalidasi kemampuan sistem dalam mengidentifikasi lagu berdasarkan kontennya.
2. Goals
   - Membangun Sistem Rekomendasi Musik. Kode Python yang dikembangkan berhasil mengimplementasikan seluruh alur kerja Content-based Filtering, dari pemuatan data hingga generasi rekomendasi, sehingga tujuan pembangunan sistem telah tercapai.
   - Memanfaatkan Fitur Konten Musik. Proyek ini berhasil mengekstraksi, memproses (TF-IDF, Scaling), dan menggabungkan berbagai fitur konten (teks dan audio) dari dataset untuk membentuk representasi vektor yang digunakan sebagai dasar rekomendasi.
   - Menghasilkan Rekomendasi yang Relevan. Melalui perhitungan Cosine Similarity pada vektor fitur konten, sistem mampu mengidentifikasi lagu-lagu dengan kemiripan konten tinggi. Output demonstrasi menunjukkan bahwa rekomendasi yang dihasilkan cenderung memiliki kesamaan yang jelas pada metadata dan fitur audio dengan lagu input, yang mengindikasikan relevansi dalam konteks Content-based.
   - Melakukan Evaluasi Kualitatif. Tahap evaluasi berhasil mendemonstrasikan sistem dengan contoh rekomendasi dan menyediakan analisis kualitatif yang menjelaskan relevansi berdasarkan kesamaan konten dan skor kemiripan, memenuhi tujuan evaluasi.
3. Solution Statements
Solusi yang diusulkan, yaitu membangun sistem rekomendasi berbasis Content-based Filtering, telah sepenuhnya diwujudkan melalui implementasi kode Python yang mencakup semua langkah yang diuraikan dalam Solution Statement: pemuatan dan penggabungan data, preprocessing fitur konten (teks dan numerik), pembuatan representasi vektor gabungan, perhitungan matriks kemiripan menggunakan Cosine Similarity, pengembangan fungsi rekomendasi Top-N, dan demonstrasi hasil rekomendasi sebagai bentuk evaluasi kualitatif.

Secara keseluruhan, submission ini berhasil mengimplementasikan solusi Content-based Filtering yang secara efektif menjawab permasalahan kelebihan informasi dalam penemuan musik dengan memanfaatkan fitur konten yang kaya, mencapai tujuan pembangunan sistem yang relevan, dan mendemonstrasikan kemampuannya melalui evaluasi kualitatif.

**---Ini adalah bagian akhir laporan---**