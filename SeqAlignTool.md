# ปฏิบัติการ  Sequence Alignment Tool วิชา BT440 2/2566

อ.ดร.ศศิพร ทองแม้น

*เอกสารอ้างอิง*
- https://ftp.ncbi.nlm.nih.gov/pub/factsheets/HowTo_BLASTGuide.pdf
- https://www.ebi.ac.uk/services
- http://www.clustal.org/omega/

### กิจกรรมที่ 1
**set path ของโปรแกรม clustal omega ใน google cloud shell ของนักศึกษา**
1. log in ที่ `console.cloud.google.com` และเลือกปุ่ม activate cloud shell
2. ตอนนี้อยู่ที่ `~` ใช้คำสั่ง `whereis clustalo` สังเกตผลลัพธ์
3. พิมพ์คำสั่ง `clustalo --help` และอีกบรรทัด `./clustalo --help` สังเกตผลลัพธ์
4. ตอนนี้อยู่ที่ `~` ให้คัดลอกและ back up ไฟล์ ดังคำสั่ง `cp .bashrc bashrc.bk`
5. เปิดไฟล์ด้วย nano editor ดังนี้ `nano .bashrc`  
   1. เพิ่ม 
   ```bash
    alias lla='ls -la'
   ```
  
   2. และไปท้ายสุด เพิ่ม 
   ```bash
   PATH=$PATH:$HOME/myclustalo:$HOME/blast/bin
   ```
   3. กด ctrl ค้างไว้แล้วกด x (ctrl + x) มันจะถามเซฟไล์มั้ย? 
      1. ให้กด y 
      2. แล้วกด enter จะออกมาที่ command prompt แปลว่า เซฟไฟล์เรียบร้อย
6. โหลดแและรัน `source .bashrc`
7. ทดสอบสิ่งที่ได้แก้ไข 
      1. พิมพ์ `lla` สังเกตผลลัพธ์
      2. พิมพ์ `whereis clustalo`
      3. พิมพ์ `clustalo --help`

### กิจกรรมที่ 2
**ลงโปรแกรม blast บน google cloud shell ของนักศึกษา**
1. ที่  `~` ดาวน์โหลด blast จาก ncbi: https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST 
    ```bash
    wget https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.15.0+-x64-linux.tar.gz
    ```
2. แตกไฟล์ด้วย คำสั่ง `tar `
    ```bash
    tar -xzvf ncbi-blast-2.15.0+-x64-linux.tar.gz
    ```
3. เปลี่ยนชื่อโฟลเดอร์เป็น `blast`
    ```bash
    mv ncbi-blast-2.15.0+ blast
    ```
4. ที่  `~` และทดลองเรียกโปรแกรม `blastp`
    ```bash
    blastp -help
    ```
5. ลบไฟล์ *.tar.gz เพื่อประหยัดเนื้อที่    
    ```bash
    rm ncbi-blast-2.15.0+-x64-linux.tar.gz
    ```
6. ทดลองรัน `blastn` แบบ remote ที่โฟลเดอร์ `~/blast` 
   1. `cd ~/blast`
   2. รันโดยใช้ database ชื่อ "rRNA_typestrains/16S_ribosomal_RNA" ที่อยู่บน ncbi และใช้ query เป็นไฟล์ fasta ที่นักศึกษาได้รับ โดย upload ไปไว้ที่ `~/blast` 
   3. รัน 
    ```bash
    blastn -db "rRNA_typestrains/16S_ribosomal_RNA" -query my16S_query_xxxxxxxxxx.fasta -outfmt 7 -max_target_seqs 10 -remote > blastout-xxx.tab
    ```    
7. ทดลองรัน blastn บน web service ของ ncbi https://blast.ncbi.nlm.nih.gov/Blast.cgi
   1. ใช้ query เป็นไฟล์ fasta ที่นักศึกษาได้รับ
   2. เลือก database: 16S ribosomal RNA
   3. ตั้งค่า max_target_seqs = 10
8.  สังเกตผลลัพธ์จาก web service โดยดาวน์โหลด Hit table(text) และจาก blast CLI แบบ remote
       - จาก blastout-xxx.tab และผลจากเว็บ คอลัน์ที่เท่าไหร่ คือ % identity, e-value  และ Accession ตามลำดับ
       - ผล 10 ลำดับ เหมือนกันหรือไม่ จากทั้ง 2 ไฟล์ผล จงอภิปราย

   
### กิจกรรมที่ 3
**ทดลองรัน clustal omega และ EMBOSS stretcher ใน web service บน embl-ebi**
1. ไปที่ https://www.ebi.ac.uk/jdispatcher หรือ https://www.ebi.ac.uk/services หาเครื่องมือ `EMBOSS stretcher` หรือ  `stretcher`
   1. เลือก DNA type 
   2. ใช้ไฟล์ตัวอย่าง 
   3. รันและสังเกตผลลัพธ์

2. ไปที่ https://www.ebi.ac.uk/jdispatcher หรือ https://www.ebi.ac.uk/services หาเครื่องมือ `Clustal Omega` 
   1. เลือก DNA type
   2. upload ไฟล์ชนิด multi-fasta 
   3. ตั้งค่า parameter เพิ่มเติมนั่นคือ ให้แสดงผลลัพธ์ distance matrix ออกมา (default ไม่ได้แสดง)
   4. รันและสังเกตผลลัพธ์

### กิจกรรมที่ 4
**รัน clustal omega และ ใน google cloud shell ของนักศึกษา**
1. จากกิจกรรมที่ 3 ดัดแปลง command ที่แสดงในแท็บผล Submission Details

    ยกตัวอย่างเช่น 
    ```bash
    clustalo --infile clustalo-job-p1m.sequence --threads 8 --MAC-RAM 8000 --verbose --guidetree-out clustalo-job-p1m.dnd --distmat-out clustalo-job-p1m.matrix --full --full-iter --outfmt clustal --resno --outfile clustalo-job-p1m.clustal_num --output-order tree-order --seqtype dna
    ```  
    (แทนที่ job ด้วยตัวเลขไอดีที่แสดงผลออกมาจาก web servicce)

    กลายเป็นคำสั่งบน  google cloud shell ของนักศึกษา ดังนี้ 
    ```bash
    clustalo --infile Block01.fasta --verbose --guidetree-out Block01.dnd --distmat-out Block01.matrix --full --full-iter --outfmt clustal --resno --outfile Block01.clustal_num --output-order tree-order --seqtype dna
    ```  
    สั่งรันที่ `~/myclustalo` โดยมีไฟล์ input คือ Block01.fasta
2. สังเกตผลลัพธ์ว่า ผลลัพธ์ที่ได้บน google cloud shell มี่กี่ไฟล์ แต่ละไฟล์เทียบได้กับผลจาก web service ไฟล์ใดกับไฟล์ใด

### การบ้าน 
- กำหนดการปล่อยการบ้านช่วงเย็นวันศุกร์ที่ 26 ม.ค. 67   
  - เข้าไปที่ https://auth.dugga.com กดปุ่ม microsoft เพื่อ log-in ด้วย อีเมล tu ของนักศึกษา หรือเข้าแอพ dugga ใน MS TEAMS


