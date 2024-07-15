## Dataset yang digunakan

Mengumpulkan dan mengimpor lebih dari 500 gambar untuk Dataset Deteksi Manusia dari Kaggle dan sumber-sumber lainnya. Dataset ini kemudian dianotasi dengan kotak pembatas dan dipublikasikan di Roboflow. Kami hanya menggunakan satu label kelas: "orang".

## Pengujian Model
Menggunakan model YOLOv8 khusus untuk deteksi objek dari Ultralytics.YOLOv8 menggunakan arsitektur convolutional neural network (CNN) yang dioptimalkan untuk deteksi objek secara real-time.Arsitektur ini dirancang untuk deteksi satu tahap, yang berarti bahwa prediksi kotak pembatas dan kelas objek dilakukan dalam satu kesimpulan.Berikut ini adalah rincian langkah-langkah model:
1. Unggah dataset ke Google Drive
2. Pasang Google Colab di Google Drive
3. Mengimpor dataset dari drive
4. Pasang GPU yang diperlukan (Tesla T4 atau Nvidia CUDA) untuk mempercepat pemrosesan gambar
5. Tentukan model YOLOv8 untuk pelatihan
6. Mulai pelatihan menggunakan model dan dataset (membutuhkan waktu 20 menit), kemudian dapatkan model terlatih (`best.pt` dan `last.pt`)
7. Plot loss dan akurasi dari model yang dilatih
8. Uji model dengan contoh gambar dan video

## Hasil Pelatihan

Berikut adalah hasil pelatihan model YOLOv8 yang dilatih dengan CUDA versi 12.1.
![GAMBAR](https://github.com/C241-PS261-LuminaSense/.github/blob/be5e91f47077610f77bccb3205489e4bf23aa1a3/assets/image1.jpg)
![GAMBAR](https://github.com/C241-PS261-LuminaSense/.github/blob/be5e91f47077610f77bccb3205489e4bf23aa1a3/assets/image2.jpg)

### Metrik Kinerja
1. **Presisi 0,916**: Presisi menunjukkan persentase deteksi positif yang benar-benar positif. Dalam hal ini, 91,6% dari kotak yang ditarik oleh model sebagai objek adalah objek yang terdeteksi (positif sejati). Nilai ini menunjukkan bahwa model jarang melakukan deteksi positif palsu (menandai "orang" padahal sebenarnya bukan "orang").
2. **2. *Recall 0.852**: Recall juga cukup tinggi, yaitu 85.2%. Hal ini menunjukkan bahwa model berhasil mendeteksi sebagian besar objek yang ada di dalam gambar dan hanya melewatkan beberapa objek (false negative).
3. **mAP50 0.923**: mAP50 (rata-rata Precision Rata-rata) adalah rata-rata presisi model pada ambang batas IoU 0.5 pada kurva precision-recall. Nilai 0,923 menunjukkan bahwa model memiliki tingkat akurasi yang tinggi dalam mendeteksi objek dalam gambar secara keseluruhan.
4. **mAP50-95 0.717**: mAP50-95 (mean Average Precision) adalah presisi rata-rata model pada rentang ambang batas 50% hingga 95% IoU pada kurva precision-recall. Nilai 0,717 menunjukkan bahwa model memiliki presisi yang lebih rendah dalam mendeteksi objek pada tingkat kepercayaan yang lebih rendah. Hal ini dapat disebabkan oleh beberapa faktor seperti objek yang kecil, objek yang terhalang, atau objek dengan pencahayaan yang buruk.

### Contoh hasil pengujian model pada sebuah foto:
![GAMBAR](https://github.com/C241-PS261-LuminaSense/.github/blob/be5e91f47077610f77bccb3205489e4bf23aa1a3/assets/image3.jpg)
