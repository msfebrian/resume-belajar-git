
# Ganti nama file dan folder dengan git
## Mengganti nama dengan git mv
## 🔗 Links
[Mengganti nama dengan git mv](https://www.patrick-wied.at/blog/rename-files-and-folders-with-git)


Untuk mengganti nama file atau folder, gunakan perintah git mv. git mv membutuhkan setidaknya dua argumen, sumber dan tujuan. Jika Anda ingin memindahkan beberapa file ke satu jalur, Anda dapat menentukan n sumber tetapi argumen terakhir adalah tujuannya.
Inilah yang sebenarnya dilakukan 'git mv':

```
mv oldfolder newfolder
git add newfolder
git remove oldfolder
```
Ia melakukan pemindahan file, menambahkan file baru ke indeks dan menghapus file lama darinya. Kita dapat melihat tidak ada komit sehingga kita harus menambahkan pembaruan dan melakukan perubahan setelahnya.

## Cara Penggunaan
Dengan asumsi Anda ingin mengubah nama folder dari folder lama ke folder baru

```
git mv oldfolder newfolder
```

Jika sudah ada folder baru di repo Anda dan Anda ingin menimpanya gunakan –force

```
git mv -f oldfolder newfolder
```
Jangan lupa: Anda harus menambahkan perubahan pada indeks dan mengkomitnya setelah mengganti nama dengan git mv.

```
git add -u newfolder
git commit -m "changed the foldername whaddup"
```
Opsi -u pada perintah add penting di sini, ini akan memperbarui file/folder yang sudah dilacak.
Ini adalah kasus penggunaan yang cukup sederhana dan dapat berfungsi hampir setiap saat. Kecuali, dan inilah bagian yang menarik:

Mengganti nama folder menjadi nama folder pada sistem file yang tidak peka huruf besar-kecil
Mengapa ini lebih menarik? Karena penggantian nama sederhana dengan perintah mv normal (bukan git mv) tidak akan dikenali sebagai perubahan file dari git. Jika Anda mencobanya dengan perintah 'git mv' seperti pada baris berikut

```
git mv foldername folderName
```

Jika Anda menggunakan sistem file yang tidak membedakan huruf besar dan kecil, misalnya Anda menggunakan Mac dan tidak mengonfigurasinya menjadi peka huruf besar/kecil, Anda akan menerima pesan kesalahan seperti ini: fatal: mengganti nama 'nama folder' gagal: Argumen tidak
valid

Dan inilah yang dapat Anda lakukan untuk membuatnya berfungsi:
```
git mv foldername tempname && git mv tempname folderName
```

Ini membagi proses penggantian nama dengan mengganti nama folder pada awalnya menjadi nama folder yang sama sekali berbeda. Setelah mengganti namanya menjadi nama folder yang berbeda, folder tersebut akhirnya dapat diubah namanya menjadi Nama folder baru. Setelah 'git mv' itu, sekali lagi, jangan lupa untuk menambahkan dan melakukan perubahan. Meskipun ini mungkin bukan teknik yang indah, teknik ini berfungsi dengan baik. Sistem file masih tidak mengenali perubahan huruf besar-kecil, tetapi git mengenalinya karena mengganti namanya menjadi nama folder baru, dan hanya itu yang kami inginkan :)

## Pengamatan menarik lainnya

git mv memiliki opsi perintah yang disebut '–dry-run' (singkatnya: '-n') yang seharusnya menunjukkan perubahan apa yang akan dilakukan jika Anda menjalankan perintah, tetapi perintah tersebut tidak akan dijalankan. Lucunya jika Anda mengganti nama folder/file dengan opsi -n:

```
git mv -n foldername folderName
```

itu akan menunjukkan perubahan yang harus terjadi (bahkan pada sistem file yang tidak peka huruf besar-kecil) sehingga menurut Anda semuanya akan berfungsi dengan baik tetapi menjalankannya tanpa -n akan gagal pada sistem file yang tidak peka huruf besar-kecil.

Oke, sejujurnya.. itu tidak terlalu menyakitkan, tapi untuk penggantian nama yang sederhana, banyak waktu debugging yang saya habiskan untuk itu.

