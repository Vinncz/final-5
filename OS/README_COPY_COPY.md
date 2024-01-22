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

> **Pertanyaan yang diingat:**
> 1. Apakah setiap row of data bisa di-uniquely identifiable?
> 2. Datanya tersortir? Pakai format apa?
> 3. Datanya bisa panjang/pendek? Kalo butuh lebih, taro dimana
> 4. Akses datanya pakai algoritma apa?

1. **Pile**
   
   - Tidak pakai ID
   - Data disortir berdasarkan kapan dibuatnya
   - Data may vary in length
   
2. **Sequence**
   
   - Pakai ID yang uniquely identifies setiap record
   - Data disortir berdasarkan alphanumerical value pada kolom ID-nya
   - Data's length is fixed; setiap baris memegang jumlah kolom data yang sama; dan kolom disetiap baris adalah sama.
   
3. **Indexed**
   
   - Tidak pakai ID
   - Data tidak tersortir -- hanya, ditampilan indexnya, data mungkin appear to be sorted
   - Data may vary in length - data yang berlebihnya disimpan di overflow file
   
4. **Indexed Sequence**
   
   - Tidak pakai ID
   - Data disortir berdasarkan bagaimana nampaknya di index. Jika di index value A dan B bersebelahan, maka di `indexed sequence` datanya pasti akan bersebelahan
   - Data may vary in length - data yang berlebihnya disimpan di overflow file
   
5. **Direct/Hash**
   
   - Tidak pakai ID
   - Data disortir berdasarkan hasil hashing yang didapat dari memasukkan value "key" sebagai argument ke hasher
   - Data may vary in length
   

ㅤ

### Disc Scheduling (hitungan)
1. **FIFO**
   
   Sesuai dengan kerjaan mana yang datang.
   
2. **SSTF Shortest Seek Time First**
   
   - tunggu sampai semua kerjaan sudah sampai
   - mulai dari posisi kursor sekarang, SELALU kearah job yang paling deket
   
3. **SCAN**
   
   - tunggu sampai semua kerjaan sudah sampai
   - mulai dari posisi kursor sekarang, lalu kearah job yang paling deket; AND STICK WITH SAID DIRECTION until udah gaada job di arah itu:
   - at which point you do a u-turn, kearah job yang paling deket
   
4. **C-SCAN**
   
   - tunggu sampai semua kerjaan sudah sampai
   - mulai dari posisi kursor sekarang, lalu kearah job yang paling deket; AND STICK WITH IT FOR THE REST OF EXECUTION.
   - ketika udah gaada job di arah itu; pindahin kursor ke posisi job YANG PALING JAUH: at which point you mengikuti arah yang diawal tadi, menyelesaikan sisa job yang ada.

ㅤ

### Memory Partitioning
1. **Fixed**
   
   - Memory sudah dipartisi dari awal
   - Setiap partisi sudah ditentukan besarnya dari awal
   - Ada 2 cara:
     - Perbolehkan process yg lebih kecil request-sizenya untuk occupy partisi yang lebih besar
     - Implementasi queue system: dimana process harus mengisi slot yang most closely resembles size yang dia request.
   
2. **Dynamic**
   
   - Memory belum dipartisi dari awal
   - Setiap partisi dibuat saat ada process yang request untuk besarnya segitu
   - Ketika process di-release, dia meninggalkan partisi yang dia request sebelumnya -- yang bisa di-coallesce menjadi partisi yang lebih besar apabila space yang bersebelahan dengannya juga kosong
   
3. **Buddy System**
   
   - Memory belum dipartisi dari awal
   - Setiap partisi besarnya pasti `2^n`
   - Partisi yang bersebelahan dan kosong bisa di-coallesce JIKA DAN HANYA JIKA gabungan dari size mereka adds up to `2^n`

ㅤ

### Placement Algo
1. **First Fit**
   
   Mulai dari index-0 memory, pas ketemu tempat yang unoccupied, langsung masuk kesitu regardless size-nya kegedean banget atau kegedean aja
   
2. **Best Fit**
   
   Mulai dari index-0 memory, carilah tempat yang most closely resembles size yang di-request sama process; dan masukkan kesitu.
   
3. **Next Fit**
   
   Mulai dari posisi cursor sekarang, lihat kedepan dan langsung pilih tempat pertama yang muat.

ㅤ

### (Replacement Algo) Virtual Memory Management Basic Algorithms
1. OPT
   
   - The only algo to look forward
   - Hanya evict page yang bakal kepakainya paling belakangan
   
2. LRU
   
   - Hanya evict page yang sudah lama tidak di-update/paling lama masuknya
   
3. FIFO
   
   - Hanya evict page yang paling lama masuknya
   
4. CLOCK
   
   - Buat dua array ADDRESSES dan ACTIVITY
   - ...

ㅤ

### Computer Security (System Call & File Access)
1. chmod(file_path, mode_t)
2. chown(file_path, uid_t, gid_t)

```cpp
int main (int argc, char* argv[]) {
    
    if ( argc != 2 ) {
        printf("Invalid argument count");
        return -1;
    }
    
    int retval = chmod(argv[1], 0644);
    if ( retval < 0 ) {
        printf("Could not chmod the file");
        return -1;
    }
    
}
```

ㅤ

### Cloud 

1. SaaS
1. IaaS
1. PaaS
