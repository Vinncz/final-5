ㅤ
ㅤ
# UAS Operating System

\
__Made for:__
> _Operating System_
>
> [ LEC ] -  Final Semester

\
__Composed by:__
> 2501977941 - Kevin Gunawan
>
> ChatGPT (Best Boi)
>
> Bard (Good Boi)

ㅤ

## Essay & Case

> Bawa penggaris dan kalkulator

### Common File Organization Types
1. Pile
   
   - Data **may NOT be uniform** in size
   - Data disortir berdasarkan kapan ia dibuat
   - **TIDAK pakai id**
   - Nyari data dengan **`exhaustive linear search`**
   
2. Sequence
   
   - **Data IS uniform**: consisting of fixed-length records, dengan jumlah kolom yang sama di setiap baris data
   - Data disortir berdasarkan alphanumeric ascending (mulai dari A, berakhir dengan Z)
   - **Pakai id**
   - Nyari data dengan **`exhaustive linear search`** untuk IDENTIFIER yang match.
   
3. Indexed
   
   - Data **may NOT be uniform** in size.
   - Data tidak tersortir
   - **TIDAK pakai id**; `key` pada index act as id
   - Nyari lokasi data-nya via **`exhaustive linear search`** ataupun **`binary search`** pada index, lalu langsung pergi ke alamat yang ditunjukkan pada index.
   - Data yang berlebih disimpan didalam `overflow file`
   - Meskipun pada index data terlihat bersebelahan, kemungkinan besar data disimpan dalam posisi yang TIDAK bersebelahan. 
   
4. Indexed Sequence
   
   - Data **may NOT be uniform** in size.
   - Data tersortir sedemikian rupa; sebagaimana ada tercatat pada index
   - **TIDAK pakai id**; `key` pada index act as id
   - Nyari lokasi data-nya via **`exhaustive linear search`** ataupun **`binary search`** pada index, lalu langsung pergi ke alamat yang ditunjukkan pada index.
   - Data yang berlebih disimpan dalam `overlfow file`
   
5. Direct/Hash
   
   - Data **may NOT be uniform** in size
   - Data tersortir (disimpan) pada lokasi yang ditentukan oleh proses Hashing pada kolom `key`-nya.
   - **TIDAK pakai id**
   - Nyari lokasi data-nya via Hashing value `key` untuk mendapatkan posisinya di storage.

ㅤ

### 4 Type Disc Scheduling (hitungan)
1. **[FIFO] First In First Out**
   
   Pindahkan seeker sesuai dengan process mana yang datang duluan.
   
2. **[SSTF] Shortest Seek Time First**
   
   - Tunggu sampai seluruh job list sudah sampai.
   - Mulai dari posisi awal, ke arah job yang TERDEKAT.
   - Lanjutkan terus hingga job-nya habis: untuk SELALU ke arah job yang TERDEKAT.
   
3. **SCAN**
   
   - Tunggu sampai seluruh job list sudah sampai.
   - Mulai dari posisi awal, ke arah job yang TERDEKAT.
   - Lanjutkan terus ke arah itu hingga job di arah tsb habis -- at which point putar balik dan target job yang TERDEKAT dari sana.
   
4. **C-SCAN**

   - Tunggu sampai seluruh job list sudah sampai.
   - Mulai dari posisi awal, ke arah job yang TERDEKAT.
   - Lanjutkan terus ke arah itu hingga jon di arah tsb habis -- at which point arahkan seeker ke job yang PALING JAUH dari posisi seeker sekarang.
   - Mulai lagi kerjain ke arah awal.
ㅤ

### Fixed and Dynamic Partitioning, Buddy System
1. **FIXED**
   
   - Memory sudah dipartisi dari awal
   - Besarnya partisi sudah ditentukan
   - Masukkan process ke manapun yang best-fit them.
   
2. **DYNAMIC**
   
   - Memory BELUM dipartisi dari awal
   - Besarnya partisi ditentukan saat ada process baru yang request sebesar yang ia butuhkan
   - Saat process di-release, mereka meninggalkan partisi sebesar yang apa mereka request.
   - Partisi yang kosong DAN BERSEBELAHAN bisa di-coallesce menjadi SATU YANG BESAR.
   - Bisa menghasilkan masalah: dimana partisi yang ia tinggalkan meng-restrict process yang lebih besar untuk muat kesitu; sehingga menyisakan tempat.
   
3. **BUDDY SYSTEM**
   
   - Memory BELUM dipartisi dari awal
   - Besarnya partisi ditentukan dengan `2^n` {1024} -> {512, 512} -> {256, 256, 256, 256} -> ...
   - Partisi yang kosong DAN BERSEBELAHAN bisa di-coallesce menjadi SATU YANG BESAR **`IF AND ONLY IF`** jumlah mereka menjadi salah satu suku dari `2^n`.

ㅤ

### (Replacement Algo) Virtual Memory Management Basic Algorithms
1. **[OPT] Optimal**
   
   - Selalu lihat kedepan: tendang siapapun yang akan dipakainya **PALING NANTI**.
   
2. **[LRU] Least Recently Used**
   
   - Tendang siapapun yang **masuk paling awal** -- JIKA DAN HANYA JIKA ia **sudah lama TIDAK DIPAKAI**
   
3. **[FIFO] First In, First Out**
   
   - Tendang siapapun yang **masuk paling awal** -- REGARDLESS apakah ia barusan dipakai/tidak
   
4. **CLOCK**
   
   - Mulai dengan membuat 2 array: namakan mereka ADDRESSES dan ACTIVITY dengan size yang sama.
   - Setiap ada page baru yang masuk, set value di array ACTIVITY menjadi 1.
   - Setiap page baru masuk, cursor HARUS dipindahkan ke posisi selanjutnya.
   - Setiap cursor melewati sebuah page, value di array ACTIVITY untuk page itu dijadikan 0.
   - Ketika page yang sama minta dimasukkan ulang, buat value di array ACTIVITY untuk page tsb jadi 1.

ㅤ

### Computer Security (System Call & File Access)
```pascal
DICTIONARY
------------------

mode_t: Arithmetic type used for file attributes.
uid_t: Arithmetic type used for user IDs.
gid_t: Arithmetic type used for group IDs.


oct      meaning
---      -------
01   ->  execute
02   ->  write
03   ->  write & execute
04   ->  read
05   ->  read & execute
06   ->  read & write
07   ->  read & write & execute

0644 means
-------------
owner: read & write
group: read
other: read

NOTE: in C, the initial "0" indicates octal notation, whereas "0x" indicates hexadecimal notation
```

\
**`chmod(file's_path, mode_t)`** is a function that allows user to set a permission associated with a file.


```cpp
mode_t var1 = 0644;
int retval = chmod("", mode_t);

if ( retval < 0 ) {
    printf("Could not chmod the file!");
}
```

\
**`chown(file's_path, uid_t, gid_t)`** is a function that allows user to set the group/owner of a file.

```cpp
uid_t = ;
gid_t = ;
int retval = chown("", uid_t, gid_t);

if ( retval < 0 ) {
    printf("Could not chmod the file!");
}
```


ㅤ

### Cloud 
