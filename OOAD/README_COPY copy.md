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
Derajat yang menunjukkan seberapa suatu code menembak langsung ke concrete implementation; ketimbang interface yang memungkinkan implementation tersebut untuk ada.
\
\
High coupling means kalau codenya akan susah diganti, seakan lego bricks yang nempelinnya pakai lem.
\
\
**HIGH BAD, LOW GOOD**

> **Cohesion**:\
Derajat yang menunjukkan seberapa bagus sebuah code bisa kerjasama dengan code lain.
\
\
High cohesion digambarkan dengan code yang mendelegasikan tugas yang tepat, ke class lain yang terspecialize untuk meng-handle tugas tsb.
\
\
**HIGH GOOD, LOW BAD**

> **Connascence**:\
Derajat yang menunjukkan seberapa relatednya attribut di suatu class.
\
\
High connascence means kalau attribute" corelated.
\
\
**NO GOOD OR BAD**

ㅤ

### System and User Interface
...

ㅤ

### Designing Tests
Tujuan dari test adalah u/ memastikan jika code yang ditulis behave as expected.

Behave as expected means jika code tersebut bebas dari error.

Ada 3 macam error:
1. Compile err
   
   Gabisa di compile
   
2. Runtime err
   
   Meledak pas dijalanin
   
3. Logic err
   
   Jalan kayak normal, tapi hasil yang dikeluarkan salah
ㅤ

Untuk membuat sebuah test, lu perlu:
1. Plan the test
   1. Objective test ini apa?
   2. Kriteria untuk lulus apa?
   3. Constraint apa yang akan acompany testnya?
   
2. Tipe tes yang mana?
   1. Unit test
      
      Nguji SATU class/method.
      
      - Blackbox testing
  
         pas GATAU inner working.
         
         fokus ke "apakah ia bisa handle, sanitize, validate, dan process input"
         
      - Whitebox testing
        
        pas TAU inner working
        
        fokus ke "gimana codenya bisa dibagusin"
      
   2. Integration test
      
      Nguji MULTIPLE class/method, mengukur kerjasamanya.
      
   3. System test
      
      Nguji keseluruhan class/method (integration test, but broader).
      
   4. Acceptance test
      
      Nguji apakah software yang didevelop memenuhi kepuasan client. (kelarin semua use case?)
      
      a. Alpha test
      
         dummy data, pakai edge cases untuk probing masalah yang terlewat
      
      b. Beta test
      
         real data, u/ diagnosis gimana sistem berjalan saat ia nanti di deploy

### Developing Documentation

Dokumentasi adalah penjelasan dari sistem. Plain and simple.

Dokumentasi ada karena:
1. lu gabisa bikin sesuatu yang terstruktur apabila tidak ada bayangan/plan akan apa yang mau lu bikin
2. orang perlu bimbingan untuk mempelajari suatu sistem; dan tidak semua orang bisa luangin waktu utk itu.
3. orang bisa lupa; bahkan pembuat sistem itu sendiri.

Dokumentasi dibagi 2:
1. System docs
   
   - targetin system maintainer/developer
   - bahas tentang gimana sistemya tertata
   - sebagai reference utk develop system kedepannya, dan gimana maintain apa yang sudah ada
   
2. User docs
   
   - targetin end-user
   - bahas tentang gimana user bisa pakai (operate) something di sistem


ㅤ

## Case

### 1.) Analysing Architecture
Architecture ngebahas tentang SOFTWARE APA JALAN DI HARDWARE APA.

6 pertanyaan utama:
- mahalan sewa/beli hardware?
- banyak biaya tambahan?
- gampang develop disitu?
- fitur/kapabilitasnya banyak?
- security ketat?
- scalable?

ada 2 komponen
- Software
  
  bahas ttg
  - data storage
  - data access logic
  - app logic
  - presentation logic
  
- Hardware
  
  bahas tentang
  - siapa clientnya?
  - spec server?
  - network apa yang bisa hubungin client-server

Ada 3 architecture utama
- server-oriented
  
  - server kerjain semua
  - client handle presentation logic
  
- client-oriented
  
  - client kerjain semua
  - server handle data storage dan retrieval
  
- server-client
  
  dibagi jadi beberapa tier:
  - 2 tier
    
    1 server u/ data storage & access logic
    client u/ app & presentation logic
    
  - 3 tier
    
    1 server u/ data storage & access logic
    1 server u/ app logic
    client u/ presentation logic
    
  - n tier
ㅤ
    n server u/ data storage
    n server u/ data access logic
    n server u/ app logic
    client u/ presentation logic

ㅤ

### 2.) Infrastructure Design in Deployment Diagram & Network Model

Deploy diag ngebahas tentang hubungan `software apa jalan di hardware apa` dan `hubungan antar hardware`.

Deploy diag fokus ke struktur "apa, dimana"; sehingga memudahkan maintenance dan mapping apa yang jalan dimana.



Network model ngebahas ttg hubungan `hardware dengan hardware`, baik itu di satu lokasi, atau antar lokasi.

Network model fokus ke metode apa yang ngehubunginnya.
