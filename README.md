
# Contouring 

Pendeteksi tepi menghasilkan citra tepi yang berupa citra biner (pixel tepi 
berwarna putih, sedangkan pixel bukan-tepi berwarna hitam). Tetapi, tepi 
belum memberikan informasi yang berguna karena belum ada keterkaitan 
antara suatu tepi dengan tepi lainnya. Citra tepi ini harus diproses lebih lanjut 
untuk menghasilkan informasi yang lebih berguna yang dapat digunakan dalam 
mendeteksi bentuk-bentuk sederhana (misalnya garis lurus, lingkaran, elips, dan 
sebagainya) pada proses analisis citra.



Praktikum terlampir di file Project UAS Adinda_088.ipynb
dengam image gambaruas.jpg

# Langkah Pengerjaan
#### 1. Ambil foto sesuai dengan ketentuan 
#### 2. Masukan Foto ke file jupyter 
#### 3. Buat File baru untuk pengerjaan projek UAS 
#### 4. Import Library yang digunakan :
- import cv2: Digunakan untuk pengolahan gambar
- import numpy as np: penggunaan as bearti pemanggilan numpy diganti dengan np, numpy berfungsi untuk membentuk objek N-dimensional array
- import matplotlib.pyplot as plt : digunakan  untuk menciptakan visualisasi yang menarik dan informatif untuk memahami data.
#### 5. Masukan file gambar yang akan di baca 
```
gambar = cv2.imread('gambaruas.jpg')
```
>> Digunakan untuk membaca file 'gambaruas.jpg' sebagai gambar 
#### 6. Mengubah gambar ke grayscale

```
abu_abu = cv2.cvtColor(gambar, cv2.COLOR_BGR2GRAY)
```
>> Mengubah gambar ke grayscale untuk mengurangi noise pada citra dan mempertahankan tepi gambar
#### 7. Lakukan Operasi untuk mendeteksi bagian tepi pada gambar
```
tanda_tepi = cv2.Canny(abu_abu, 30, 150)
```
>> cv2.Canny untuk mendeteksi tepi gambar
#### 8. Deteksi Kontur pada gambar

```
kontur, _ = cv2.findContours(tanda_tepi, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```
>> cv2.RETR_EXTERNAL untuk mengekstraksi kontur luar pada objek gambar
#### 9. Tampilkan kontur gambar
```
cv2.drawContours(gambar_asli, kontur, -1, (0, 0, 255), 3)
```
>> digunakan untuk menggambar kontur menggunakan library openCV, dimana kontur akan digambar menggunakan warna merah 
#### 10. Tampilkan hasil gambar dan gambar asli menggunakan subplot 
```
fig, ax = plt.subplots(1, 2, figsize=(10, 5))
```
>> Menampilkan gambar dalam subplot 
- #### Menampilkan gambar asli pada subplot pertama
```
ax[0].imshow(cv2.cvtColor(gambar, cv2.COLOR_BGR2RGB))
x[0].set_title('Gambar Asli')
```
>> Subplot pertama menampilkan gambar asli 

- #### Menampilkan gambar dengan kontur pada subplot kedua
```
ax[1].imshow(cv2.cvtColor(gambar_asli, cv2.COLOR_BGR2RGB))
ax[1].set_title('Gambar Contour')
```
>> Subplot kedua menampilkan gambar yang sudah di beri Contour

