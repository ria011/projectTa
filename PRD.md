# Product Requirements Document (PRD) - Sistem Input Nilai Tugas Akhir

## 1. Introduction

### 1.1 Purpose
Merancang dan mengembangkan sistem web untuk manajemen input nilai Tugas Akhir (TA) yang aman, terkontrol, dan terintegrasi. Sistem ini menggantikan penggunaan Google Forms yang memiliki masalah keamanan, di mana siapa saja dengan link dapat menginput nilai TA untuk mahasiswa dan dosen yang tidak terkait.

### 1.2 Scope
**Included:**
- Sistem manajemen pengguna dengan role-based access (Admin, Dosen)
- Modul penjadwalan TA
- Modul input nilai TA berdasarkan jadwal yang telah dibuat
- Validasi data dan kontrol akses berbasis role

**Excluded:**
- Sistem akademik non-TA saat ini
- Integrasi dengan sistem kepegawaian

### 1.3 Definitions, Acronyms, and Abbreviations
- **TA**: Tugas Akhir / Skripsi
- **Admin**: Administrator sistem
- **Dosen Pembimbing**: Dosen yang membimbing mahasiswa TA
- **Dosen Penguji**: Dosen yang menguji hasil TA
- **Role-Based Access Control (RBAC)**: Sistem kontrol akses berdasarkan peran

## 2. Product Overview

### 2.1 Product Summary
Sistem web berbasis PHP terbaru untuk manajemen input nilai Tugas Akhir dengan kontrol akses berbasis role, validasi data ketat, dan antarmuka yang user-friendly. Sistem ini memastikan hanya dosen pembimbing dan penguji yang terdaftar untuk mahasiswa tertentu yang dapat menginputkan nilai.

### 2.2 Product Vision
Menciptakan ekosistem manajemen nilai TA yang aman, transparan, dan efisien dengan mengeliminasi risiko kesalahan input dan unauthorized access.

### 2.3 Business Objectives
1. Meningkatkan keamanan dan integritas data nilai TA
2. Mengurangi risiko input nilai oleh pihak yang tidak berwenang
3. Mempermudah proses manajemen penjadwalan dan penilaian TA
4. Meningkatkan efisiensi administrasi TA
5. Menyediakan audit trail untuk setiap input nilai

## 3. Target Audience

### 3.1 User Personas
1. **Admin**: Pengelola sistem, mengelola user, jadwal TA, dan laporan
2. **Dosen Pembimbing**: Menginput nilai dan mengawasi perkembangan TA mahasiswa bimbingannya
3. **Dosen Penguji**: Menginput nilai ujian TA untuk mahasiswa yang dijadwalkan

### 3.2 User Needs
**Admin:**
- Kemampuan membuat, mengubah, dan menghapus user
- Assign role kepada user
- Melihat laporan lengkap aktivitas sistem

**Dosen Pembimbing & Penguji:**
- Input nilai dengan mudah untuk TA yang dijadwalkan
- Hanya dapat input nilai untuk mahasiswa yang relevan
- Konfirmasi data mahasiswa dan jadwal sebelum input nilai
- Kemampuan melihat dan edit nilai yang telah diinput

## 4. Features and Functionality

### 4.1 Core Features
1. **Manage User & Role**
   - CRUD user (Create, Read, Update, Delete)
   - Assign role (Admin, Dosen)
   - Manage akses dosen terhadap mahasiswa

2. **Input Penjadwalan TA**
   - Buat jadwal ujian TA dengan detail mahasiswa, dosen pembimbing, dosen penguji
   - Edit dan delete jadwal
   - Calendar view untuk melihat jadwal TA

3. **Input Nilai TA**
   - Form input nilai dengan validasi
   - Hanya dosen yang terjadwal yang dapat input
   - Proses approval/validasi nilai
   - View history nilai yang diinput

### 4.2 Feature Details
**F1. Manage User & Role**
- Create user baru dengan email, nama, role assignment
- Edit profil user, password, dan role
- Deactivate/activate user
- Assign dosen ke mahasiswa (pembimbing/penguji)

**F2. Input Penjadwalan TA**
- Form penjadwalan dengan field: nama mahasiswa, NIM, dosen pembimbing, dosen penguji, tanggal ujian, ruangan
- Validasi duplikasi jadwal
- Notifikasi email ke dosen yang dijadwalkan

**F3. Input Nilai TA**
- Form input nilai dengan kriteria (pembimbing, penguji)
- Kolom input: nilai komponen (presentasi, laporan, tanya jawab, dll)
- Validasi range nilai (0-100)
- Submit dan review nilai sebelum finalisasi

## 5. Functional Requirements

### 5.1 Manage User & Role
- FR1.1: Admin dapat membuat user baru dengan email dan password
- FR1.2: Admin dapat mengassign role (Admin/Dosen) ke user
- FR1.3: Admin dapat mengubah data user (nama, email, role)
- FR1.4: Admin dapat menonaktifkan user tanpa menghapus data
- FR1.5: User dapat mengubah password sendiri
- FR1.6: Admin dapat assign dosen sebagai pembimbing/penguji untuk mahasiswa tertentu
- FR1.7: Sistem mencatat history perubahan user dan role

### 5.2 Input Penjadwalan TA
- FR2.1: Admin dapat membuat jadwal TA baru
- FR2.2: Form penjadwalan harus mencakup: NIM/nama mahasiswa, dosen pembimbing, dosen penguji, tanggal, waktu, lokasi
- FR2.3: Sistem validasi tidak boleh ada jadwal duplikasi untuk mahasiswa yang sama
- FR2.4: Sistem validasi tidak boleh ada jadwal bentrok untuk dosen yang sama
- FR2.5: Admin dapat mengubah dan menghapus jadwal (terutama sebelum jadwal berlangsung)
- FR2.6: Sistem mengirim notifikasi email ke dosen pembimbing/penguji saat jadwal dibuat
- FR2.7: Fitur calendar view untuk melihat seluruh jadwal TA
- FR2.8: Fitur filter/search jadwal per mahasiswa, dosen, atau tanggal

### 5.3 Input Nilai TA
- FR3.1: Hanya dosen pembimbing/penguji yang dijadwalkan dapat mengakses form input nilai
- FR3.2: Form input nilai hanya muncul untuk TA yang sudah dijadwalkan
- FR3.3: Form input nilai mencakup komponen penilaian (presentasi, laporan, tanya jawab, dsb)
- FR3.4: Sistem validasi nilai harus range 0-100 dan numerik
- FR3.5: Dosen dapat menyimpan draft sebelum submit
- FR3.6: Setelah submit, nilai dapat di-review oleh admin sebelum finalisasi
- FR3.7: Dosen dapat melihat history nilai yang telah diinput
- FR3.8: Sistem mencatat timestamp dan user yang melakukan input nilai

## 6. Non-Functional Requirements

### 6.1 Performance
- Page load time maksimal 2 detik
- Form submission response time maksimal 3 detik
- Support minimal 100 concurrent users
- Database query optimization untuk handling 10,000+ records data mahasiswa

### 6.2 Security
- Authentication: Login dengan email dan password (enkripsi bcrypt minimum)
- Authorization: Role-based access control (RBAC)
- Data validation: Input sanitization dan escaped untuk mencegah SQL injection
- HTTPS/SSL untuk semua komunikasi
- Session management dengan timeout 30 menit
- Audit log untuk semua aktivitas critical (login, input nilai, perubahan user)
- Password policy: minimum 8 karakter, kombinasi huruf, angka, simbol
- Rate limiting untuk brute force protection

### 6.3 Usability
- Responsive design untuk desktop dan mobile
- Clear error messages dan validasi form real-time
- Intuitive navigation dan user interface
- Tooltips dan help sections untuk setiap fitur
- Dark mode option (optional)

### 6.4 Compatibility
- Browser: Chrome, Firefox, Safari, Edge (versi terbaru)
- Responsive pada screen size: desktop, tablet, mobile (≥375px)
- Cross-platform: Windows, macOS, Linux

## 7. User Stories

### Admin
- As an admin, I want to create new user accounts untuk dosen dan staff yang baru bergabung.
- As an admin, I want to assign role dan permission agar setiap user memiliki akses yang sesuai dengan jabatannya.
- As an admin, I want to see activity log semua perubahan data untuk audit purposes.
- As an admin, I want to manage penjadwalan TA dan assign dosen pembimbing/penguji.

### Dosen Pembimbing
- As a dosen pembimbing, I want to input nilai TA untuk mahasiswa yang saya bimbing saja.
- As a dosen pembimbing, I want to see daftar mahasiswa saya yang sudah dijadwalkan ujian TA.
- As a dosen pembimbing, I want to edit nilai yang saya input jika ada kesalahan.

### Dosen Penguji
- As a dosen penguji, I want to input nilai ujian TA untuk mahasiswa yang dijadwalkan dengan saya.
- As a dosen penguji, I want to hanya bisa input nilai pada jadwal TA saya saja, bukan TA mahasiswa lain.
- As a dosen penguji, I want to see detail mahasiswa dan jadwal sebelum input nilai.

## 8. Acceptance Criteria

### Manage User & Role
- ✅ Admin dapat membuat user dengan validasi email yang benar
- ✅ Password di-hash dengan bcrypt, tidak tersimpan plaintext
- ✅ Setiap perubahan user tercatat di audit log dengan timestamp
- ✅ User tidak dapat mengubah role sendiri
- ✅ Email verifiction dikirim ke user baru untuk confirm akun

### Input Penjadwalan TA
- ✅ Jadwal tidak dapat duplikat untuk mahasiswa yang sama
- ✅ Jadwal tidak dapat bentrok untuk dosen yang sama
- ✅ Notifikasi email dikirim ke dosen pembimbing dan penguji
- ✅ Admin dapat melihat kalender seluruh jadwal TA
- ✅ Edit/delete jadwal hanya bisa dilakukan sebelum jadwal berlangsung

### Input Nilai TA
- ✅ Hanya dosen yang dijadwalkan dapat mengakses form input nilai
- ✅ Nilai harus numeric, range 0-100
- ✅ Timestamp dan user ID tercatat untuk setiap input
- ✅ Dosen dapat menyimpan draft dan melanjutkan kemudian
- ✅ Admin dapat mereview nilai sebelum finalisasi
- ✅ Nilai yang sudah finalized tidak dapat diubah tanpa approval admin

## 9. Assumptions and Constraints

### 9.1 Assumptions
- Semua dosen memiliki email institusi yang aktif
- Sistem akan terintegrasi dengan data mahasiswa existing (atau manual input)
- Admin akan melakukan training untuk dosen pre-launch
- Semua pengguna memiliki koneksi internet yang stabil
- Data backup dilakukan secara regular oleh IT department

### 9.2 Constraints
- Development menggunakan PHP latest version (v8.1+)
- Budget dan timeline sudah didefinisikan
- Server infrastructure sudah tersedia
- Email server sudah terkonfigurasi untuk pengiriman notifikasi
- Tidak ada integrasi dengan sistem legacy yang kompleks

## 10. Timeline and Milestones

### Phase 1: Requirement & Design (Minggu 1-2)
- ✅ Finalisasi PRD dan approval stakeholder
- Desain database dan system architecture
- Desain UI mockup

### Phase 2: Development (Minggu 3-6)
- Database setup dan migration
- Backend development (API endpoints)
- Frontend development
- User & role management module
- Penjadwalan TA module
- Input nilai TA module

### Phase 3: Testing (Minggu 7-8)
- Unit testing
- Integration testing
- User acceptance testing (UAT)
- Security testing

### Phase 4: Deployment & Training (Minggu 9)
- Production deployment
- Data migration (jika ada)
- Training untuk admin dan dosen
- Go-live dan support

## 11. Risks and Mitigations

| Risk | Impact | Probability | Mitigation |
|------|--------|------------|------------|
| Data loss / corruption | Critical | Low | Regular backup, database replication, disaster recovery plan |
| Security breach / unauthorized access | Critical | Low | SSL/TLS, strong authentication, input validation, penetration testing |
| Performance degradation | High | Medium | Database optimization, caching, load testing |
| User adoption resistance | Medium | Medium | Training, clear documentation, user-friendly interface |
| Integration issues dengan data existing | Medium | Medium | Early testing, data mapping documentation, rollback plan |
| Jadwal TA konflik / duplikasi | Medium | Low | Validation logic yang kuat, admin review |
| Email notification tidak terkirim | Low | Low | Alternative notification method, monitoring sistem |

## 12. Technical Specifications

### 12.1 Technology Stack
- **Backend**: PHP 8.1+ (Framework: Laravel/CodeIgniter)
- **Frontend**: HTML5, CSS3, JavaScript (Framework: Vue.js/React optional)
- **Database**: MySQL 8.0+
- **Server**: Linux (Apache/Nginx)
- **Email**: SMTP untuk notifikasi

### 12.2 Database Schema (Overview)
- `users` - User accounts dengan role dan status
- `roles` - Role definition (Admin, Dosen)
- `permissions` - Permission mapping
- `mahasiswa` - Data mahasiswa
- `jadwal_ta` - Penjadwalan TA
- `nilai_ta` - Input nilai TA dengan komponen penilaian
- `audit_log` - Activity log untuk compliance

### 12.3 API Endpoints (Overview)
```
AUTH
- POST /api/login
- POST /api/logout
- POST /api/refresh-token

USERS (Admin)
- GET /api/users
- POST /api/users
- PUT /api/users/{id}
- DELETE /api/users/{id}

JADWAL
- GET /api/jadwal-ta
- POST /api/jadwal-ta
- PUT /api/jadwal-ta/{id}
- DELETE /api/jadwal-ta/{id}

NILAI
- GET /api/nilai-ta
- POST /api/nilai-ta
- PUT /api/nilai-ta/{id}
```

## 13. Appendices

### A. Glossary
- **TA**: Tugas Akhir / Skripsi (Final Project)
- **RBAC**: Role-Based Access Control
- **SMTP**: Simple Mail Transfer Protocol

### B. References
- Existing System: Google Forms implementation
- Security Standards: OWASP Top 10

### C. Sign-off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Manager | | | |
| Business Analyst | | | |
| Stakeholder | | | |

---

**Document Version**: 1.0  
**Last Updated**: April 5, 2026  
**Status**: Draft - Awaiting Approval