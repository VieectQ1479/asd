# Symbolic and Algebraic Reasoning in Petri Nets

**Trường:** Đại học Bách Khoa TP.HCM (HCMUT)  
**Môn học:** Mô hình hóa Toán học (Mathematical Modeling - CO2011)  
**Học kỳ:** 251 (Năm học 2025 - 2026)  
**Đề tài:** Symbolic and Algebraic Reasoning in Petri Nets

---

## 1. Giới thiệu
Dự án này là bài tập lớn nhằm xây dựng công cụ phân tích **Mạng Petri 1-safe** (1-safe Petri nets). Ứng dụng được viết bằng ngôn ngữ C++ để tối ưu hóa hiệu năng, kết hợp các kỹ thuật:
* **Explicit Search:** Duyệt không gian trạng thái bằng BFS.
* **Symbolic Search:** Sử dụng BDD (Binary Decision Diagrams) để biểu diễn không gian trạng thái lớn.
* **Deadlock Detection:** Phát hiện tắc nghẽn bằng quy hoạch tuyến tính (ILP).

## 2. Thành viên nhóm (Nhóm 41)

| STT | Họ và tên | MSSV | Vai trò |
|:---:|:---|:---:|
| 1 | Lê Tuấn Khang | 2411443|
| 2 | Nguyễn Quốc Việt | 2413952|
| 3 | Ngô Anh Khôi | 2411694|
| 4 | Nguyễn Lê Anh Xuân | 2420013|
| 5 | Dương Quang Minh | 2412034 |

## 3. Yêu cầu & Cài đặt (Prerequisites & Setup)

Dự án sử dụng **CMake** để quản lý quá trình biên dịch.

> **⚠️ Lưu ý quan trọng:**
> Mã nguồn dự án đã bao gồm sẵn mã nguồn thư viện **BuDDy** (trong thư mục `buddy/`) và thư viện **GLPK** (trong thư mục `GLPK/`). 
> **Không đổi tên hoặc di chuyển** các thư mục này để đảm bảo cấu hình CMake hoạt động chính xác.

## 4. Hướng dẫn biên dịch (Build Instructions)

### Bước 1: Tạo thư mục build và biên dịch
Mở terminal tại thư mục gốc của dự án và chạy lần lượt các lệnh sau:

```bash
mkdir build
cd build
cmake ..
cmake --build .
```

Quá trình này sẽ biên dịch mã nguồn và tự động copy các file input mẫu (.pnml) vào thư mục build.

### Bước 2: Chạy chương trình
Sau khi biên dịch thành công, file thực thi PetriNetApp sẽ xuất hiện trong thư mục build.
Đối với Windows:
# Chạy với file input mặc định
.\Debug\PetriNetApp.exe simple_lbs-5.pnml
Đối với Linux / macOS:
./PetriNetApp simple_lbs-5.pnml

## 5. Các chức năng đã thực hiện trong dự án
Task 1 - Parse PNML

Đọc file chuẩn PNML (Petri Net Markup Language).

Xây dựng cấu trúc dữ liệu Petri Net (Places, Transitions, Arcs).

Sử dụng thư viện tinyxml2

Task 2 - Explicit Reachability:

Sử dụng thuật toán tìm kiếm theo chiều rộng (BFS).

Liệt kê toàn bộ không gian trạng thái (Reachable Markings) từ trạng thái đầu.

Task 3 - Symbolic Reachability:

Mã hóa các trạng thái và hàm chuyển đổi bằng Binary Decision Diagrams (BDD).

Sử dụng thư viện BuDDy để tính toán tập trạng thái đạt được.

Báo cáo số lượng trạng thái, thời gian chạy và số node BDD sử dụng.

Task 4 - Deadlock Detection:

Kết hợp tập trạng thái đạt được (từ BDD) và phương trình trạng thái (State Equation).

Sử dụng thư viện GLPK (Integer Linear Programming) để tìm kiếm deadlock.

Xuất ra một trạng thái Deadlock cụ thể nếu tìm thấy.

Task 5 - Optimization:

Tìm trạng thái $M$ trong tập trạng thái đạt được sao cho hàm mục tiêu $c^T M$ là lớn nhất.Sử dụng thuật toán duyệt trên đồ thị BDD (Dynamic Programming) để tìm nghiệm tối ưu.
