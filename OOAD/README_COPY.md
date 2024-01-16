ㅤ
ㅤ
# UAS Object Oriented Analysis & Design

\
__Made for:__
> _Object Oriented Analysis & Design_
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

## Essay

### Coupling, Cohesion, and Connascence

> **Coupling**:\
Derajat yang menunjukkan seberapa code menembak langsung ke implementasi concrete ketimbang interface yang lebih umum.
\
\
High coupling berarti bahwa datatype yang digunakan sangatlah strict, dan akan susah diganti kedepannya.
\
\
Anggap seperti lego block yang di-lem untuk nempelinnya. Kuat sih kuat (code bisa jalan), tapi bakalan susah dipakai (didevelop kedepannya ketika mau variasikan code tsb). 
\
\
**HIGH BAD, LOW GOOD**


> **Cohesion**:\
Derajat yang menunjukkan seberapa code bekerja sama satu sama lain untuk menghasilkan result yang diinginkan.
\
\
High cohesion berarti code tsb TEAM PLAYER, dan membagi tugasnya ke class-class yang spesialisasi untuk mengerjakan tugas itu.
\
\
**HIGH GOOD, LOW BAD**

> **Connascence**:\
Derajat yang menunjukkan seberapa closely related attribut yang ada didalam class.
\
\
High connascence berarti jika satu attribut berganti value, ada beberapa yang lain yang perlu diganti juga.
\
\
**TIDAK ADA GOOD OR BAD**
ㅤ

### System and User Interface
...

ㅤ

### Designing Tests

Tujuan dibalik tes adalah agar memastikan code yang ditulis behave as expected.

Behave as expected means jika code tersebut bebas dari error-error. Terdapat 3 macam error:

1. Compilation err
   meledak saat mau di-compile. biasanya masalah di syntax.
   
2. Runtime err
   meledak immidiately saat dijalankan. biasanya masalah di initialization atau array out-of-bounds.
   
3. Logic err
   berjalan normal; tapi hasil yang dikeluarkan salah.

Untuk membuat sebuah tes, ada 2 langkah yang perlu digenapi:

1. Plan the test
   
   * objective dari test ini apa?
   * kondisi sebuah code lulus tes apa?
   * constraint apa yang membatasi code?
   
2. Select test type
   
   1. Unit test
      
      menguji SEBUAH class/method. ada 2 macam unit test:
      
      1. blackbox testing
         
         - dilakukan ketika lu GATAU INNER WORKING-nya sebuah code.
         
         - fokus ke menguji code's ability to process, sanitize, and validate an input.
         
      2. whitebox testing
         
         - dilakukan ketika lu TAU INNER WORKING-nya sebuah code.
         
         - fokus ke menguji BAGAIMANA CODE BISA DI-IMPROVISASI
      
   2. Integration test
      
      menguji sebagaimana bagus kerjasama antara MULTIPLE CODE.
      
      - user interface test
      - system interface test
      - use case test
      - interaction test
      
   4. System test
      
      menguji sebagaimana bagus sebuah code perform dalam sistem (nguji banyak class/method sekaligus)
      
   6. Acceptance test
      
      menguji apakah semua use case sudah diterapkan/ditangani oleh sistem.
      
      ada 2 macam acceptance test:
      1. Alpha
         
         menggunakan data dummy, yang nge-probe untuk kesalahan penanganan di edge-case
         
      3. Beta
         
         menggunakan data beneran, yang system bakal likely encounter saat di-deploy

ㅤ

### Developing Documentation

Documentation adalah penjelasan. Plain and simple.

Docs ada karena:
1. imagine lu punya banyak block lego (satu container)
2. lu gabisa asal pasang block-block itu menjadi sesuatu yang bagus dan terstruktur.
3. at least, lu perlu vision dan guidance tentang kira" apa yang akan dibuat, dan gimana itu tertata.
4. docs adalah jelmaan vision dan guidance itu.

atau, jika reasoning diatas ga dimengerti, liat dari sudut pandang orang yang pakai docs:
1. **orang baru**: daripada mengganggu team untuk minta diajarin, dia bisa refer ke docs untuk cari tahu
2. **veteran system**: karena udah lupa-lupa, docs bisa menjadi pengingat dan pemberi tahu gimana sistemnya tertata.
3. **troubleshooter**: 

Ada 2 macam docs:
1. System Docs
   
   - targetnya developer/maintainer
   - ngasih tau caranya develop the system further/gimana maintain it
   - menguraikan kompleksitas sistem (bagaimana kerjanya)
   
2. User Docs
   
   - targetnya ke end user
   - ngasih tau caranya operate the system

ㅤ

## Case

### 1.) Analysing Architecture
Architecture ngebahas tentang `software APA jalan di hardware APA`.

6 pertanyaan utama utk menentukan architecture:
1. mahalan beli hardware atau sewa?
2. banyak biaya tambahan di hardware itu?
3. gampang developnya disitu?
4. advantage pakai A apa kebanding pakai B?
5. apa security ketat?
6. scalable?

Architecture ada 2 komponen:
1. Software
   
   - data storage
   - data access logic
   - app logic
   - presentation logic
   
2. Hardware
   
   - client siapa?
   - spec server apa?
   - network yang hubungin server-client gimana?

3 architecture type:
1. Server
   - client terima jadi
   - server melakukan semua processing (data storage, access logic, app logic)
  
2. Client
   - server hanya SIMPAN DATA
   - kerjaan semua di client
   - mahal di network traffic
  
3. Server-client
   dibagi lagi jadi banyak tier:
   - **2 tier**
     
     1 server untuk simpen data, access logic\
     client app + presentation logic
     
   - **3 tier**
     
     1 server u/ simpen data, access logic\
     1 server u/ app logic\
     client u/ presentation logic
     
   - **n-tier**
     
     n server u/ simpan data\
     n server u/ access logic\
     n server u/ app logic\
     client u/ presentation logic

ㅤ

ㅤ

### 2.) Infrastructure Design in Deployment Diagram & Network Model
Deploy diag menggambarkan `software APA jalan di hardware MANA`, dan `hubungan ANTAR hardware`.


Deploy diag membantu untuk:
1. melihat big picture of the system
2. mengidentifikasi roadblock
3. mendasarkan reference point tentang confignya sistem
4. menyediakan strukturnya sistem secara pasti

Network model mainly menggambarkan `hubungan hardware yang ada di lokasi yang berbeda`, terkhususnya bagaimana mereka terkoneksinya (pakai LAN, protokol apa)




