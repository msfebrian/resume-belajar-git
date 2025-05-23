# alur kerja git
Work Tree --> Stagged --> History (commit)

melihat configurasi git
	git config --list
untuk keluar list
	tekan :q
unutk keluar dari text editor bawaan git (vim)
	tekan :wq

# perintah untuk membuat repository git di local
1. masuk ke folder yg akan dijadikan repository
2. ketik perintah git init

# setting repository
1. pastikan folder sudah sesuai
2. cek dgn perintah print work direktory yaitu "pwd" tanpa tanda kutip
3. jika sudah sesuai config user
	$ git config --global user.name "John Doe"
	$ git config --global user.email johndoe@example.com
jika hanya untuk local folder saja/folder yg diinginkan saja
	$ git config --local user.name "John Doe"
	$ git config --local user.email johndoe@example.com

# cara menghapus konfigurasi user git
	git config --global --unset user.name
	git config --global --unset user.mail

# untuk melihat file config
	git config --global -e

# untuk memasukkan file ke stage
- perintah untuk memasukkan semua file yg berubah--> git add .
- perintah untuk memasukkan file tertentu--> git add "nama_file"

# perintah untuk commit
	git commit -m "uraian perubahannya"

# perintah add stage sekaligus commit
	git commit -am "nama_file"

# cara cek status commit dan status synkron/up to date dan tidaknya di repository remote
	git status

# cara lihat history
	git log

# untuk file tertentu
	git log -- nama_file

# untuk melihat branch yg aktif 
	git branch

# untuk membuat branch
	git branch nama_branch

# untuk pindah branch
	git checkout nama_branch

# untuk mengembalikan file dari commit
	git log
	git checkout 5_digit_hash contoh git checkout 766b4

# untuk melihat branch yg sudah di merge
	git branch --merged

# untuk hapus branch yang sudah di merge
	git branch -d nama_branch

# untuk hapus branch yang belum di merge
	git branch -D nama_branch


# melihat graph
	git log --all --decorate --oneline --graph

# membuat perintah alias
	alias graph="git log --all --decorate --oneline --graph"
perintah diatas jadi bisa dipanggil dengan graph


# untuk tarik data/clone dari online host
	git clone url_gitnya

# cara merge branch ke master
posisi folder di master kemudian perintah git merge nama_branch
jika ada conflict perbaiki dahulu manual

# tahapan remote
	untuk melihat remote
		git remote

	untuk melihat detail alamat remote
		git remote -v 

	untuk meng add reposiroty dari local ke online host
		git remote add origin https://linkrepository_gitnya.git (nama origin bisa diganti2 dgn nama remotenya misal github/gitlab)

	untuk upload ke online (agar kedepannya tinggal perintah push saja)
		git push -u nama_remote nama_branch contoh git push -u origin master

# untuk upload ke online host 
	git push
	
# untuk merge data dari remote & local
	git fetch (terlebih dahulu untuk cek commit)
	git pull (jika error conflict perbaiki manual terlebih dahulu 
			kemudian stage & commit git commit -am "nama_file" dan push untuk upload ke online jika ada perubahan)

## jika posisi ada 2 remote harus ditentukan nama remotenya
###  untuk fetch 
	git fetch nama_remote_git
### untuk merge
	git merge nama_remote/nama_branch

### untuk push 
	git push nama_remote nama_branch
	atau 
	untuk upload ke online (agar kedepannya tinggal perintah push saja)
	git push -u nama_remote nama_branch contoh git push -u origin master

### untuk hapus branch diremote 
	git push nama_remote --delete nama_branch
	contoh = git push origin --delete feature

# Perbedaan git fetch dan Pull
	perintah git pull di gunakan saat tidak ada commit yang pernah dilakukan di lokal. 
	Sedangkan perintah git fetch digunakan kalau sudah ada commit yang dilakukan. 
	Penggunaan git fetch lebih aman, karena kita akan melakukan merge branch secara manual. Sehingga kita bisa terhindar dari bentrokan.
			
# Github Pages
untuk membuat webhosting gratis gi github buat repository dengan format berikut:
username.github.io beri deskripsi kemudian public dan jgn buat readme
untuk menambahkan repository dalam github page.. masuk ke repository --> setting --> github pages --> pilih source branchnya
cara aksesnya username.github.io/nama_repository
jika ingin alamatnya berbeda untuk domain pilih custom domain di setting


## fork adalah menduplikat repository lain


# CATATAN PROBEM SOLVING TESTED WORK
================================================================
Jika gagal commit dari repository dari hasil clone
dan tampil seperti ini
	*** Please tell me who you are.
	
	Run
	
	  git config --global user.email "you@example.com"
	  git config --global user.name "Your Name"
	
	to set your account's default identity.
	Omit --global to set the identity only in this repository.
	
	fatal: unable to auto-detect email address (got 'blah@blah.(none)')

GUNAKAN PERINTAH INI DAN PASTIKAN GLOBAL/LOCAL username dan email sudah terkonfigurasi
	git -c user.name="Your Name" -c user.email="you@example.com" commit -m "message"

=================================================================

# CARA LAINNYA
Set config for this/current repo only just remove --global and set name/email like this:

	$ git config user.name "John Doe" 
	$ git config user.email "JohnDoe@gmail.com" 

kemudian
	GIT_AUTHOR_EMAIL="you@email.com" && GIT_AUTHOR_NAME="Your Name" && git commit

# merubah repository public ke private
1. masuk ke repository pilih icon pengaturan
2. cari visibility di menu paling bawah rubah ke private
