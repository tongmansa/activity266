# ปฏิบัติการ  Machine Learning Tool วิชา BT440 2/2566
อ.ดร.ศศิพร ทองแม้น

## การเทรนโมเดลการเรียนรู้แบบมีผู้สอน (Supervised ML)
เทรนโมเดลด้วยแพลตฟอร์ม https://teachablemachine.withgoogle.com ซึ่งเฟรมเวิร์คในการเทรนโมเดลใช้วิธีการแบบ transfer learning กล่าวคือนำเอา pretrained model มาเป็นจุดเริ่มต้นในการเทรนข้อมูลนำเข้าของผู้เทรนโมเดล โดยแพลตฟอร์มนี้มีวัตถุประสงค์เพื่อให้ทุกคนสามารถเข้าใจขั้นตอนการเทรนโมเดลด้วยข้อมูลภาพ ข้อมูลวิดีทัศน์ หรือข้อมูลเสียง  
ในปฏิบัติการนี้จะใช้ชุดข้อมูลภาพจากชุดข้อมูลสารธารณะหรือข้อมูลจากเว็บแคมเป็นข้อมูลนำเข้า

#### ภาพที่ 1 จาก https://github.com/googlecreativelab/teachablemachine-community/
<img src="https://github.com/googlecreativelab/teachablemachine-community/blob/master/teachablemachine.gif?raw=true" style="width: 100%;">

### ชุดข้อมูลสำหรับกิจกรรม
- https://tinyurl.com/CNXRayBT440 เฉพาะโฟลเดอร์ `val`
- https://tinyurl.com/animalfBT440 
- https://tinyurl.com/fruit360BT440 ยกเว้นโฟลเดอร์ fruit-360-original-size

### กิจกรรม
1. การเทรนโมเดลด้วยข้อมูลจากเว็บแคมและรูปภาพ
- การนำเข้าข้อมูล
	- ภาพจากเว็บแคมหรือจากโฟลเดอร์ `train`
- การเทรนโมเดลและพารามิเตอร์สำหรับการเทรน
	- แท็บ Adavance
- ข้อมูลสอนและข้อมูลทดสอบที่ใช้สำหรับในระหว่างเทรน 
- ข้อมูลที่นำมาเพื่อใช้สาธิตการทำนาย (ไม่ใช่ภาพที่นำไปเทรน)
	- ภาพจากเว็บแคมหรือจากโฟลเดอร์ `Test` (ถ้ามี) มิฉะนั้นเลือกภาพจากโฟลเดอร์ `val`
2. การเซฟโมเดลและสาธิตการนำไปใช้งานบน colaboratory (*.ipynb)


#### แหล่งที่มาของชุดข้อมูลสาธารณะ 
- https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia
- https://www.kaggle.com/datasets/andrewmvd/animal-faces
- https://www.kaggle.com/datasets/moltean/fruits?select=fruits-360_dataset

### การบ้านในไฟล์ระหว่างเวลาเรียน