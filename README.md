# Image Enhancement from Scratch

Notebook pembelajaran untuk implementasi image enhancement pada **spatial domain** dan **frequency domain** menggunakan Python.

Algoritma pengolahan piksel dibuat manual. `PIL` hanya digunakan untuk membaca gambar dan `matplotlib` untuk menampilkan gambar serta histogram.

## Menjalankan Notebook

1. Buka `CVL_Assignment01.ipynb` di VS Code atau Jupyter Notebook.
2. Pastikan kernel Python tersedia.
3. Jalankan cell secara berurutan.
4. Setiap cell teknik memiliki path gambar sendiri yang dapat diubah langsung.

Dependensi:

```bash
pip install pillow matplotlib
```

## Materi

Notebook mencakup:

- Konversi grayscale dan histogram
- Image negative
- Log transform dan inverse log transform
- Piecewise-linear transform
- Contrast stretching
- Gray-level slicing
- Histogram equalization
- Linear weighted filter
- Smoothing dan averaging filter
- Gaussian filter 5x5
- Median filter 5x5
- Laplacian sharpening 5x5
- Unsharp masking
- Image averaging
- Image subtraction
- Fourier transform 2D manual
- Frequency-domain low-pass filter
- Frequency-domain high-pass filter

Setiap hasil ditampilkan bersama histogram input dan histogram hasil.

## Pemetaan Gambar

| Teknik | Input | Permasalahan yang Ditangani |
|---|---|---|
| Image negative | `bright.png` | Membalik intensitas citra terang |
| Log transform | `dark.png` | Memperjelas detail pada citra gelap |
| Inverse log transform | `bright.png` | Transformasi intensitas citra terang |
| Piecewise-linear dan contrast stretching | `lowcontrast.png` | Meningkatkan kontras rendah |
| Gray-level slicing | `highconstrast.png` | Menonjolkan rentang intensitas tertentu |
| Histogram equalization | `lowcontrast.png` | Meratakan distribusi intensitas |
| Linear, averaging, Gaussian, median | `noise.png` | Mengurangi noise |
| Laplacian dan unsharp masking | `blurredimage.jpg` | Menajamkan citra blur |
| Fourier transform | `blurredimage.jpg` | Menganalisis frekuensi citra |
| Frequency low-pass | `noise.png` | Mereduksi komponen frekuensi tinggi/noise |
| Frequency high-pass | `blurredimage.jpg` | Menonjolkan detail dan tepi |
| Image averaging | `noise.png` + `bright.png` | Menggabungkan dua input |
| Image subtraction | `bright.png` + `dark.png` | Melihat perbedaan dua citra |

## Mengubah Input

Pada cell teknik, ubah nilai path seperti berikut:

```python
image_path = os.path.join(ROOT, 'noise.png')
gray = load_grayscale(image_path)
show_image_histogram(gray, 'Grayscale input')
```

Untuk operasi dua gambar:

```python
image_path_1 = os.path.join(ROOT, 'noise.png')
image_path_2 = os.path.join(ROOT, 'bright.png')
```

Semua filter spasial yang digunakan pada notebook memakai kernel 5x5. Fourier transform menggunakan citra 32x32 agar DFT manual tetap dapat dijalankan dengan waktu yang wajar.
