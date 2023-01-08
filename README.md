# SIG_TEORI_TGS8
 working with terrain data
 
 # Langkah Kerja :

1. Pergi ke USGS Earthexplorer. Di tab Kriteria Pencarian, klik Fitur Dunia. Di Feature Name masukkan Everest, di Country masukkan NEPAL, klik Show. Ini akan menampilkan tabel dengan informasi lokasi. Pilih Everest di bawah Nama Tempat.

2. Sekarang kanvas akan pindah ke lokasi Gunung Everest. Klik pada Kumpulan Data.

3. Perluas grup Digital Elevation, dan periksa GMTED2010. Klik pada Hasil.

4. Click the Download Options button.

5. Pilih opsi 30 ARC SEC dan klik Unduh. Anda sekarang akan memiliki file bernama GMTED2010N10E060_300.zip. Data elevasi didistribusikan dalam berbagai format raster seperti ASC, BIL, GeoTiff, dll. QGIS mendukung berbagai format raster melalui pustaka GDAL. Data GMTED datang sebagai file GeoTiff yang terkandung dalam arsip zip ini. Untuk kenyamanan, Anda dapat mengunduh salinan data langsung dari bawah. GMTED2010N10E060_300.zip

6. Buka Lapisan Tambah Lapisan Tambahkan Lapisan Raster.

7. Klik pada … di bawah Sumber, cari dan pilih file bernama 10n060e_20101117_gmted_mea300.tif.

8. Anda akan melihat data medan yang ditampilkan di Kanvas QGIS. Setiap piksel dalam raster medan mewakili ketinggian rata-rata dalam meter di lokasi tersebut. Piksel gelap mewakili area dengan ketinggian rendah dan piksel yang lebih terang mewakili area dengan ketinggian tinggi.

9. Mari temukan bidang minat kita. Dari Wikipedia, kami menemukan bahwa koordinat untuk area yang kami minati - Gunung Everest - terletak pada koordinat 27.9881° LU, 86.9253° BT. Perhatikan bahwa QGIS menggunakan koordinat dalam format (X, Y), jadi Anda harus menggunakan koordinat sebagai (Bujur, Lintang). Tempelkan 86.9253,27.9881 ini di bagian bawah jendela QGIS di mana tertulis Koordinasi dan tekan Enter. Area pandang akan dipusatkan pada koordinat ini. Untuk memperbesar, Masukkan 1:1000000 di bidang Skala dan tekan Enter. Anda akan melihat viewport zoom ke area sekitar Himalaya.

10. Kami sekarang akan memotong raster ke area yang diminati ini. Cari Klip di Processing Toolbox. Pilih Clip Raster berdasarkan luasnya di bawah algoritma GDAL.

11. Di jendela Clip Raster by Extent, pilih 10n060e_20101117_gmted_mea300 sebagai Input Layer, klik ... di Clipping extent dan pilih Use Map canvas extent, klik ... di Clipped (extent) dan masukkan nama sebagai mt_everest.tif. Klik Jalankan.

12. Lapisan baru mt_everest akan muncul di kanvas. Cari Hill di Processing Toolbox. Pilih algoritma Hillshade di bawah algoritma GDAL.

13. Di jendela Hillshade, pilih mt_everest sebagai Elevation Layer, masukkan 315.000 di Azimuth (sudut horizontal), masukkan 45.000 di sudut Vertikal. Klik ... di Hillshade dan masukkan namanya sebagai mt_everest_hillshade.tif. Klik Jalankan.

14. Lapisan baru mt_everest_hillshade akan muncul di kanvas.

15. Cari Kontur di Processing Toolbox. Pilih algoritma Kontur di bawah algoritma GDAL.

16. Di jendela Contour, pilih mt_everest sebagai Input Layer, masukkan 250 di Interval antara garis kontur. Klik ... di Contours dan masukkan namanya sebagai mt_everest_contour.gpkg. Klik Jalankan.

17. Lapisan baru mt_everest_contour akan muncul di kanvas. Klik kanan pada layer dan klik Open Attribute Table.

18. Anda akan melihat bahwa setiap fitur baris memiliki atribut bernama ELEV. Ini adalah ketinggian dalam meter yang diwakili oleh setiap garis. Klik pada tajuk kolom beberapa kali untuk mengurutkan nilai dalam urutan menurun. Di sini Anda akan menemukan garis yang mewakili elevasi tertinggi dalam data kami, yaitu Gunung Everest.

19. Pilih baris atas, dan klik tombol Zoom to selection.

20. Beralih ke jendela QGIS utama. Anda akan melihat garis kontur yang dipilih disorot dengan warna kuning. Ini adalah area elevasi tertinggi dalam dataset kami.

21. Cari Smooth di Processing Toolbox. Pilih Halus di bawah geometri Vektor.

22. Di jendela Smooth, pilih mt_everest_contour sebagai Input Layer, masukkan 5 di Iterasi. Klik Jalankan.

23. Sebuah layer baru Smoothed akan muncul di kanvas. Lapisan ini akan memiliki tepi yang lebih halus dibandingkan dengan lapisan mt_everest_contour.

24. Anda juga dapat memvisualisasikan lapisan kontur dan memverifikasi analisis Anda dengan mengekspor lapisan kontur sebagai KML dan melihatnya di Google Earth. Klik kanan pada layer yang dihaluskan, pilih Export Save Feature As….

25. Pilih Bahasa Markup Lubang Kunci [KML] sebagai Format. Klik ... di File name dan masukkan namanya sebagai contour_smoothed.kml. Klik Oke.

26. Jelajahi file keluaran pada disk Anda dan klik dua kali untuk membuka Google Earth Pro.
 
