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

ㅤ

## Essay & Case

> Bawa penggaris dan kalkulator

### Common File Organization Types
There are 5 ways to organize a file:
1. **Pile**
   
   - Seperti naruh baju kotor di keranjang.
    
   - Hanya kumpulan data yang ditata berdasarkan kapan data tsb dibuat.
   
   - Ukurannya gak uniform, bisa lebih gede/kecil dari yang lain
    
   - Bisa nyari suatu data dengan mencarinya satu-per-satu.
   
2. **Sequence**
   
   - Paling sering ditemui; **`KAYAK SQL`** (setiap baris terdiri dari jumlah kolom yang sama, dengan urutan kolom yang sama)
   
   - Digunakan untuk menampung records, yang masing-masingnya punya id
   
   - Digunakan di batch application
   
3. **Index**
   
   - Bisa pakai variable-length records.
   
   - Semua records didata di index, sehingga size nya bisa besar.
   
   - Imagine you have a huge stack of notebooks filled with notes for different subjects. Finding a specific note can be a pain, right? Indexed file organization is like having a handy cheat sheet with the page numbers for each topic.

   - Here's how it works:

     Each notebook gets a label: This is like the record key, a unique identifier for each notebook (e.g., "Biology - Photosynthesis").
     
     \
     You create a separate list: This is the index, where you write down the notebook labels and the page numbers where they start.
     
     \
     Now, finding a specific note is easy: Just check the index for the topic (e.g., "Photosynthesis"), see the page number, and flip straight to it! No more flipping through mountains of notes.
     
     \
     Indexed file organization works the same way in computers. Instead of notebooks and notes, we have files and records. The index helps us find specific records quickly, without scanning through the entire file like reading every page of a notebook.
     
     \
     This is especially useful when you have a massive dataset, like a library catalog or your music collection. Imagine trying to find a specific book or song without an index – it would take forever!
     
     \
     So, indexed file organization is like a magic map for files, helping us find what we need in a flash, even in the biggest collection!
   
4. **Indexed Sequence**

   - Sama kayak index method, bedanya index disini ga akurat, hanya ngasih approximate location dimana sebuah record disimpan.
   
   - TLDR: meskkipun ada index, lu harus cari manual lagi.
   
   - Bisa jadi pros, sebab index tidak menjadi terlalu besar, sehingga lebih cepat dicari.

5. **Direct or Hash**
   
   - Menggunakan fixed-length records.
   
   - Langsung mengakses block of a known address, lalu bandingkan hash dengan record yang disimpan untuk mencari datanya.


ㅤ

### 4 Type Disc Scheduling (hitungan)
- **First Come First Serve (FCFS)**
  
  ![FCFS](https://media.geeksforgeeks.org/wp-content/uploads/20190727015526/fcfs-1.jpg)
  
  Sesuai dengan urutan kerjaan dateng.
  
- **Shortest Seek Time First (SSTF)**
  
  ![SSTF](https://media.geeksforgeeks.org/wp-content/uploads/3333-4.png)
  
  Sesuai mana yang terdekat.
  
- **Scan**
  
  ![SCAN](https://media.geeksforgeeks.org/wp-content/uploads/20190727175932/fcfs-2.jpg)
  
  Mulai ke arah kerjaan yang paling deket.
  
  Lurus terus sampai job di arah itu habis, lalu putar balik.
  
- **C-Scan**
  
  ![CSCAN](https://media.geeksforgeeks.org/wp-content/uploads/20190820015715/fcfs2.png)
  
  Mulai ke arah kerjaan yang paling deket.
  
  Lurus terus sampai job di arah itu habis, lalu mentokin ke job paling jauh dari posisi kursor sekarang.
  
  Ikuti arah yang didapat dari awal.
  

ㅤ

### Fixed and Dynamic Partitioning, Buddy System
![Fixed partitioning](image-3.png)

Setiap block sudah dipartisi dari awal, dengan size yang predetermined.

![Dynamic partitioning](image-2.png)

Setiap block dialokasi pas dapet process, dengan size yang sesuai dengan process tsb.

Ketika process tsb selesai, partisi tsb tidak hilang.

![Buddy system](image-1.png)

Pakai 2^n untuk memecah setiap block.


ㅤ

### Virtual Memory Management Basic Algorithms
![Alt text](image.png)

| Algorithm                      | Conditions                                                                                                                 |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| **OPTIMAL (OPT)**              | ketika full, ganti apa yang ada dengan page address yang masih jauh bakal kepakainya                                       |
| **LEAST RECENTLY USED (LRU)**  | ketika full, ganti apa yang ada, dengan page address yang paling last-to-date (pas angka-nya sama, update 'kesegarannya')  |
| **FIRST IN, FIRST OUT (FIFO)** | ketika full, ganti apa yang ada, dengan page address yang paling last-to-date (pas angka-nya sama, BIARKAN 'kesegarannya') |
| **CLOCK**                      | God, help me on this one.                                                                                                  |


ㅤ

### Computer Security (Coding)
`chmod(file's_path, mode_t)` is a fucntion that allows user to set a permission associated with a file.

`chown(file's_path, uid_t, gid_t)` is a function that allows user to set the group/owner of a file.

\
**Dengan datatype:**

`mode_t`: Arithmetic type used for file attributes.

`uid_t`: Arithmetic type used for user IDs.

`gid_t`: Arithmetic type used for group IDs.

\
**Contoh penggunaan:**
```cpp
#include<iostream>
#include<sys/stat.h>
#include<sys/types.h>

using namespace std;
int main (int argc, char* agrv[]) {
    
    if ( argc != 2 ) {
        cout << "Incorrect usage" << endl;
        return 1;
    }
    
//               ↓  mencoba mengganti permission sebuah file
    int retval = chmod(argv[1], 0644);
    if ( retval < 0 ) {
        cout << "Could not chmod the file" << endl;
        return 1;
    }
    
    return 0;
}

```

ㅤ

### Cloud (belajar yang umum)
This is Cloud (belajar yang umum)!


ㅤ

