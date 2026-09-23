# Klasifikasi Aksara Jawa (Da, Ta, Sa, Wa, La) Menggunakan Convolutional Neural Network (CNN)

## Deskripsi Proyek
Proyek ini membangun sistem klasifikasi lima karakter aksara Jawa (Da, Ta, Sa, Wa, La) yang memiliki kemiripan visual tinggi menggunakan Convolutional Neural Network (CNN). Lima skenario preprocessing diuji (baseline, Otsu, median+Otsu, morfologi, skeletonization). Skenario terbaik (exp4_skeleton) mencapai akurasi 97,5% dengan loss 0,0730, jauh mengungguli baseline yang hanya 20%.

## Tujuan
- Membangun sistem klasifikasi aksara Jawa tulisan tangan berbasis CNN.
- Menguji pengaruh lima skenario preprocessing terhadap performa model.
- Membandingkan hasil dengan penelitian terdahulu (LVQ: 66,66%, OCR+LBP: 89,4%).

## Tools & Library
- Python 3
- TensorFlow, Keras (CNN)
- OpenCV (image processing)
- Scikit-image (skeletonization)
- Scikit-learn (metrik evaluasi)
- NumPy, Matplotlib (manipulasi & visualisasi)
- Google Colab

## Tahapan Proyek
1. **Akusisi Data** - Unduh dataset Hanacaraka dari Kaggle (5 kelas: da, ta, sa, wa, la, 391 citra)
2. **EDA** - Distribusi kelas, statistik ukuran, visualisasi sampel
3. **Preprocessing** - 5 skenario: baseline, Otsu, median+Otsu, morfologi closing, skeletonization
4. **Split & Augmentasi** - 80:10:10 (stratified), augmentasi rotasi/shift/zoom 10%
5. **Pembangunan Model CNN** - 3 blok konvolusi (32, 64, 128 filter) + Dense 256 + Dropout 0,5
6. **Training** - EarlyStopping (patience=10) + ModelCheckpoint
7. **Evaluasi** - Accuracy, precision, recall, F1-score, confusion matrix

## Hasil
| Eksperimen | Akurasi | Loss |
|---|---|---|
| baseline | 20,00% | 1,6097 |
| exp1_otsu | 92,50% | 0,1676 |
| exp2_median_otsu | 92,50% | 0,2258 |
| exp3_full | 95,00% | 0,2425 |
| **exp4_skeleton** | **97,50%** | **0,0730** |

- **Skenario terbaik:** exp4_skeleton (median filter + Otsu + morphological closing + skeletonization).
- Skeletonization mereduksi variasi ketebalan stroke sehingga model lebih fokus pada pola bentuk struktural.
- Hasil 97,5% mengungguli metode LVQ (66,66%) dan OCR+LBP (89,4%) pada penelitian terdahulu.

## File Terkait
- Notebook Klasifikasi<br>(./notebook/klasifikasi_aksara_jawa.ipynb)
- Dataset: Hanacaraka (Kaggle)<br>(https://www.kaggle.com/datasets/vzrenggamani/hanacaraka)

## Author
**Fauziah Roikhana Wardah** (dan tim Kelompok 07)
- Program Studi S1 Sains Data, Universitas Negeri Surabaya
- Email: fauziahroikhana@gmail.com
