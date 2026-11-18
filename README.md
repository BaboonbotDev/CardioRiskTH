# 🫀 CardioRisk TH 

**CardioRisk TH** คือเว็บแอปพลิเคชันแบบไฟล์เดียว (Single-file HTML) ที่ทำงานแบบ Offline-first สำหรับประเมินและเปรียบเทียบความเสี่ยงโรคหัวใจและหลอดเลือด (Cardiovascular Risk) รองรับทั้งการใช้งานของประชาชนทั่วไป บุคลากรทางการแพทย์ และการวิเคราะห์ข้อมูลระดับกลุ่มประชากรสำหรับงานวิจัยทางคลินิก โดยข้อมูลทั้งหมดประมวลผลภายในเครื่องของผู้ใช้ 100% (Client-side only)

---

## 🇹🇭 คำอธิบายภาษาไทย (Thai Description)

### ภาพรวมโครงการ

การประเมินความเสี่ยงโรคหัวใจและหลอดเลือดในเวชปฏิบัติไทยและงานวิจัยมักต้องอ้างอิงหลายสมการควบคู่กัน **CardioRisk TH (Version Beta 0.5)** จึงถูกพัฒนาขึ้นเพื่อรวม 3 โมเดลหลักไว้ในหน้าจอเดียว พร้อมระบบเปรียบเทียบเกณฑ์ความเสี่ยง ปัจจัยเสริมความเสี่ยง (Risk Enhancers) ตามแนวทางเวชปฏิบัติล่าสุด และเครื่องมือวิเคราะห์ทางสถิติสำหรับชุดข้อมูลผู้ป่วยขนาดใหญ่โดยไม่ต้องเขียนโค้ดหรือส่งข้อมูลออกนอกเครื่อง

### ฟีเจอร์หลัก (Key Features)

* **โหมดประชาชนทั่วไป (General Public Mode):** ประเมินความเสี่ยงด้วยคำถามเข้าใจง่าย 9 ข้อ (ใช้สูตรไม่เจาะเลือดได้) แสดงผลแบบ Icon Array (จำนวนคนใน 100 คน) จำลองการลดความเสี่ยงเบื้องต้น แจ้งเตือนค่าวิกฤต และสร้างการ์ดรูปภาพสำหรับส่งต่อให้แพทย์ทาง LINE หรือแชร์ลงโซเชียลมีเดียโดยไม่ระบุชื่อผู้ป่วย


* **โหมดบุคลากรทางการแพทย์ (Clinician Mode - มีระบบรหัสผ่าน):**
* **Multi-Model Assessment:** คำนวณและเปรียบเทียบ 3 สมการพร้อมกันบนสเกลเดียว ได้แก่ **Thai CV Risk Score** (Rama-EGAT / MOPH HDC ทั้งแบบใช้ผลเลือด TC และไม่ใช้ผลเลือด Waist-to-Height ratio), **SCORE2 Asia-Pacific** (แสดงผลเทียบทั้ง 4 Risk regions) และ **AHA PREVENT** (Base model ทั้งความเสี่ยง 10 ปี และ 30 ปี สำหรับ ASCVD, Total CVD และ Heart Failure พร้อมคำนวณ eGFR ด้วยสมการ CKD-EPI 2021)


* **Clinical Guidelines & Risk Enhancers:** รองรับการประเมินปัจจัยเสริมความเสี่ยงและเป้าหมาย LDL-C อ้างอิงตามแนวทางเวชปฏิบัติไทย (RCPT 2024), ESC 2021 และ ACC/AHA


* **Dynamic Vector Infographic & What-If Simulator:** แผนภาพหัวใจและหลอดเลือดจำลองตามระดับความดันโลหิตและไขมันของผู้ป่วย พร้อมแถบเลื่อน (Sliders) จำลองผลลัพธ์เมื่อปรับลดปัจจัยเสี่ยงแบบ Real-time


* **Local Patient History:** บันทึกและติดตามแนวโน้มความเสี่ยงตามเวลาด้วยรหัสผู้ป่วย (เก็บข้อมูลใน `localStorage` ของเบราว์เซอร์เท่านั้น)




* **โหมดวิจัยทางคลินิก (Research & Cohort Analytics):**
* นำเข้าไฟล์ `.csv` ของกลุ่มผู้ป่วยพร้อมระบบจับคู่คอลัมน์อัตโนมัติ (Auto-column mapping) และจัดการข้อมูลสูญหายแบบ Complete-case แยกตามโมเดล


* คำนวณสถิติความสัมพันธ์และความสอดคล้องระหว่างโมเดลอัตโนมัติ: **Spearman's ρ**, **Pearson's r** (บน log scale), **Partial correlation** (ปรับอายุและเพศ) และ **Linearly weighted Cohen's κ** (พร้อม Bootstrap 95% CI 1,000 รอบ)


* ประเมินประสิทธิภาพการทำนายเมื่อมีข้อมูลเหตุการณ์จริง: **C-statistic (AUC)** พร้อม DeLong 95% CI, **Observed-to-Expected (O/E) ratio** (รองรับ Kaplan–Meier ที่ 10 ปี), **Brier score** และกราฟ Calibration plot


* **Sensitivity Analysis & Auto-Methods:** วิเคราะห์ความไวของ SCORE2-AP ทั้ง 4 Risk regions และสร้างร่างย่อหน้า **Statistical Methods** ภาษาอังกฤษสำหรับนำไปใช้ใน Manuscript ได้ทันที พร้อมส่งออกผลคำนวณรายบุคคลเป็นไฟล์ CSV




* **ระบบตรวจสอบความถูกต้องของสมการ (Built-in Equation Validation):** หน้าตรวจสอบผลการคำนวณในแอปเทียบกับค่าอ้างอิงที่ตีพิมพ์ในวารสารต้นฉบับ (Golden reference test cases)



---

## 🇬🇧 English Description

### Overview

**CardioRisk TH (Version Beta 0.5)** is a zero-dependency, single-file web application designed for 10-year and 30-year cardiovascular risk assessment, side-by-side model comparison, and offline clinical research analytics. Built with a strict privacy-first architecture, all clinical calculations and cohort statistical analyses run entirely in the browser—patient data never leaves the device.

### Key Features

* **Dual-Interface Architecture:**
* **General Public Mode:** A layperson-friendly 9-item questionnaire (supporting non-lab assessment) featuring a 100-person icon array, interactive risk-reduction toggles, clinical red-flag alerts, and an on-device canvas generator for anonymous doctor-consultation cards (LINE) and social media posters.


* **Clinician Mode (Passcode-gated):** Comprehensive clinical workspace supporting both conventional (`mg/dL`) and SI (`mmol/L`, `µmol/L`) units, bilingual toggle (Thai/English), and automatic light/dark themes.




* **Three Validated Risk Engines Side-by-Side:**
* **Thai CV Risk Score (Rama-EGAT / MOPH HDC):** Supports both laboratory (Total Cholesterol) and non-laboratory (Waist-to-Height ratio) equations.


* **SCORE2 Asia-Pacific:** Implements regional recalibrations across all four Asia-Pacific risk regions (Low, Moderate, High, Very high) with ESC 2021 age-specific thresholds.


* **AHA PREVENT (Base Model):** Computes 10-year and 30-year risks for **ASCVD**, **Total CVD**, and **Heart Failure**, with built-in race-free **CKD-EPI 2021 eGFR** and BMI calculations.




* **Guideline-Integrated Decision Support & What-If Simulation:**
* Incorporates clinical risk enhancers and LDL-C targets aligned with the **2024 Thai Dyslipidemia CPG (RCPT)**, **ESC 2021**, and **ACC/AHA guidelines**.


* Interactive What-If sliders for real-time absolute risk reduction simulation and dynamic SVG cardiovascular vector infographics.




* **In-Browser Cohort Research Suite:**
* **CSV Batch Processing:** Import cohort datasets with smart column auto-mapping and model-specific complete-case handling.


* **Correlation & Agreement:** Automatically computes **Spearman’s rank correlation (ρ)**, **Pearson’s r** on log-transformed risk, **age- and sex-adjusted partial correlations**, subgroup stratifications, and 3-tier harmonised **linearly weighted Cohen’s κ** (with 1,000-resample bootstrap 95% CIs).


* **Discrimination & Calibration:** Computes **C-statistics (DeLong 95% CI)**, **Brier scores**, and decile **calibration plots** with **O/E ratios** (supporting 10-year Kaplan–Meier observed risk when follow-up time is provided).


* **Manuscript Generator:** Automatically drafts an English **Methods & Results summary paragraph** from the active cohort and exports per-patient risk estimates to CSV.




* **Built-In Golden Validation Suite:** Includes an internal verification view testing the JavaScript engine against published worked examples from the original PREVENT, SCORE2-AP, CKD-EPI 2021, and MOPH HDC specifications.



---

## 🚀 การติดตั้งและใช้งาน (Getting Started)

ไม่ต้องติดตั้งเซิร์ฟเวอร์หรือไลบรารีเสริม (Zero dependencies) สามารถใช้งานได้ทันที:

1. ดาวน์โหลดไฟล์ HTML จาก Repository นี้


2. เปิดไฟล์ด้วยเว็บเบราว์เซอร์สมัยใหม่ทั่วไป (Chrome, Safari, Edge, Firefox) ทั้งบนคอมพิวเตอร์และสมาร์ทโฟน หรือนำขึ้นโฮสต์บน **GitHub Pages** ได้โดยตรง



---

## 📚 แหล่งอ้างอิงของสมการ (Equation References)

1. **Thai CV Risk Score:** Faculty of Medicine Ramathibodi Hospital, Mahidol University (EGAT cohort) & Ministry of Public Health (MOPH) HDC 43-file specification v1.0.


2. **SCORE2 Asia-Pacific:** SCORE2 Asia-Pacific writing group (Hageman SHJ et al.). *Eur Heart J* 2025;46(8):702–715. doi:10.1093/eurheartj/ehae609.


3. **AHA PREVENT:** Khan SS et al. Development and validation of the American Heart Association PREVENT equations. *Circulation* 2024;149:430–449. doi:10.1161/CIRCULATIONAHA.123.067626.


4. **eGFR (CKD-EPI 2021):** Inker LA et al. New creatinine- and cystatin C–based equations to estimate GFR without race. *N Engl J Med* 2021;385:1737–1749.



---

## ⚠️ ข้อจำกัดความรับผิดชอบ (Disclaimer)

แอปพลิเคชันนี้ (Version Beta 0.5) เป็นเครื่องมือช่วยสนับสนุนการตัดสินใจทางคลินิกและการศึกษาวิจัยเท่านั้น **ไม่ใช่การวินิจฉัยทางการแพทย์** การตัดสินใจรักษาขึ้นอยู่กับดุลยพินิจของแพทย์ผู้ดูแลผู้ป่วยเป็นสำคัญ

---
