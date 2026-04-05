# Interview Guide - Sistem Input Nilai Tugas Akhir

## Pendahuluan

**Tujuan Interview:** Mengumpulkan informasi detail dan klarifikasi requirement dari stakeholder untuk memastikan implementasi sistem sesuai dengan kebutuhan bisnis dan teknis.

**Audiens Interview:**
- Admin/Prodi
- Dosen Pembimbing
- Dosen Penguji
- IT Department
- Stakeholder Akademik

**Format Interview:** 30-45 menit per sesi, menggunakan pertanyaan terbuka dan closed-ended.

---

## 1. General Questions

### 1.1 Business Context
1. Bagaimana proses input nilai TA saat ini menggunakan Google Forms?
2. Masalah apa yang paling sering terjadi dengan sistem existing?
3. Berapa jumlah mahasiswa TA per semester?
4. Berapa jumlah dosen yang terlibat dalam proses TA?
5. Apakah ada regulasi atau kebijakan institusi terkait penilaian TA?

### 1.2 User Experience
1. Bagaimana pengalaman Anda menggunakan sistem existing?
2. Fitur apa yang paling penting bagi Anda dalam sistem baru?
3. Apa yang membuat frustrasi dalam proses input nilai saat ini?
4. Bagaimana Anda ingin sistem memberitahu Anda tentang jadwal TA?

---

## 2. Manage User & Role

### 2.1 Admin Perspective
1. Bagaimana proses onboarding dosen baru saat ini?
2. Siapa saja yang memiliki akses admin ke sistem?
3. Apakah ada hierarki role di antara dosen (misalnya dosen tetap vs dosen tidak tetap)?
4. Bagaimana Anda mengelola akses dosen ke mahasiswa tertentu?
5. Apakah ada kebutuhan untuk bulk import user dari sistem existing?

### 2.2 User Management Details
1. Field apa saja yang diperlukan untuk data user (nama, NIP, email, departemen)?
2. Apakah email institusi wajib digunakan?
3. Bagaimana proses reset password jika user lupa?
4. Apakah ada integrasi dengan sistem SSO institusi?

---

## 3. Input Penjadwalan TA

### 3.1 Scheduling Process
1. Siapa yang bertanggung jawab membuat jadwal TA?
2. Bagaimana proses koordinasi antara admin, dosen pembimbing, dan dosen penguji?
3. Berapa lama sebelum ujian TA jadwal harus dibuat?
4. Apakah ada template atau format jadwal yang sudah ada?
5. Bagaimana menangani perubahan jadwal mendadak?

### 3.2 Calendar & Notification
1. Fitur apa yang Anda inginkan di calendar view?
2. Jenis notifikasi apa yang diperlukan (email, SMS, in-app)?
3. Siapa saja yang perlu mendapat notifikasi?
4. Berapa lama sebelum jadwal notifikasi dikirim?

### 3.3 Validation Rules
1. Aturan apa saja untuk mencegah konflik jadwal?
2. Bagaimana menentukan dosen penguji (random, berdasarkan bidang, dll)?
3. Apakah ada batasan jumlah mahasiswa per dosen per hari?

---

## 4. Input Nilai TA

### 4.1 Grading Process
1. Komponen penilaian apa saja yang digunakan untuk TA?
2. Berapa range nilai untuk setiap komponen?
3. Apakah ada bobot berbeda untuk setiap komponen?
4. Bagaimana proses kalkulasi nilai akhir?
5. Apakah ada nilai minimum untuk lulus TA?

### 4.2 Access Control
1. Kapan dosen dapat mulai input nilai (sebelum, selama, atau setelah ujian)?
2. Berapa lama deadline input nilai setelah ujian?
3. Apakah dosen penguji dan pembimbing input nilai secara terpisah?
4. Bagaimana jika ada ketidaksepakatan nilai antara dosen?

### 4.3 Workflow & Approval
1. Apakah nilai perlu di-approve oleh admin sebelum final?
2. Siapa yang dapat melihat nilai sebelum finalisasi?
3. Bagaimana proses revisi nilai jika ada kesalahan?
4. Apakah ada audit trail yang diperlukan untuk perubahan nilai?

---

## 5. Technical Requirements

### 5.1 Integration
1. Sistem apa saja yang perlu diintegrasikan (data mahasiswa, email, dll)?
2. Format data apa yang digunakan untuk import/export?
3. Apakah ada API yang sudah tersedia dari sistem existing?

### 5.2 Performance & Scalability
1. Berapa estimasi pengguna aktif bersamaan?
2. Apakah ada peak time penggunaan sistem?
3. Kebutuhan storage untuk berapa tahun data?

### 5.3 Security & Compliance
1. Kebijakan keamanan apa yang berlaku di institusi?
2. Apakah ada requirement compliance (misalnya GDPR, ISO)?
3. Bagaimana proses backup dan disaster recovery?

---

## 6. User Interface & Experience

### 6.1 Design Preferences
1. Preferensi warna atau branding institusi?
2. Bahasa apa yang digunakan (Indonesia/English)?
3. Apakah ada logo atau asset visual yang perlu disertakan?

### 6.2 Mobile Experience
1. Apakah dosen sering mengakses dari mobile?
2. Fitur apa yang paling penting untuk mobile view?

### 6.3 Accessibility
1. Apakah ada kebutuhan accessibility khusus?
2. Bagaimana dengan dosen yang memiliki keterbatasan?

---

## 7. Implementation & Deployment

### 7.1 Timeline
1. Kapan sistem baru harus siap digunakan?
2. Apakah ada deadline akademik yang perlu diperhatikan?
3. Bagaimana proses migrasi dari sistem existing?

### 7.2 Training & Support
1. Siapa yang perlu training?
2. Berapa lama training yang diperlukan?
3. Jenis support apa yang dibutuhkan setelah go-live?

### 7.3 Testing
1. Siapa yang akan terlibat dalam UAT?
2. Skenario testing apa yang penting?
3. Bagaimana proses rollback jika ada masalah?

---

## 8. Future Considerations

### 8.1 Expansion
1. Fitur apa yang mungkin ditambahkan di masa depan?
2. Apakah sistem ini akan diintegrasikan dengan sistem akademik lain?
3. Kebutuhan reporting apa yang mungkin muncul?

### 8.2 Maintenance
1. Siapa yang akan maintain sistem setelah deployment?
2. Budget untuk maintenance dan update?
3. Kebutuhan training berkala?

---

## Template Jawaban Interview

**Nama Interviewer:** ____________________
**Tanggal:** ____________________
**Posisi Respondent:** ____________________
**Durasi Interview:** ____________________

### Ringkasan Jawaban:
[Catat poin-poin penting dari jawaban respondent]

### Follow-up Questions:
[Catat pertanyaan tambahan yang muncul selama interview]

### Action Items:
[Catat tindakan yang perlu dilakukan berdasarkan interview]

---

**Document Version:** 1.0
**Last Updated:** April 5, 2026
**Prepared by:** Development Team