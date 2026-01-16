# Chương Trình Quản Lý Nhân Viên

Một ứng dụng C++ để quản lý danh sách nhân viên sử dụng cấu trúc dữ liệu **danh sách liên kết đơn (Linked List)**.

## 📋 Mô Tả

Chương trình cung cấp các chức năng quản lý nhân viên cơ bản: nhập liệu, tìm kiếm, sắp xếp, thêm, xóa, sửa thông tin. Dữ liệu được lưu trữ trong file và có thể được đọc lại khi khởi động chương trình.

## 🎯 Tính Năng Chính

| # | Chức Năng | Mô Tả |
|----|----------|-------|
| 1 | Nhập danh sách nhân viên | Nhập thông tin từ bàn phím với kiểm tra mã trùng lặp |
| 2 | Đọc danh sách từ file | Tải dữ liệu từ file `DSNV.txt` |
| 3 | Tìm kiếm theo mã nhân viên | Tìm nhân viên bằng mã ID |
| 4 | Tìm kiếm theo tên nhân viên | Tìm kiếm theo từng phần của tên |
| 5 | Xem nhân viên lương thấp nhất | Hiển thị thông tin nhân viên có lương thực lĩnh thấp nhất |
| 6 | Sắp xếp theo lương | Sắp xếp danh sách theo lương giảm dần, lưu vào `DSNV_SAPXEP.txt` |
| 7 | Xóa nhân viên | Xóa nhân viên theo mã, lưu thông tin xóa vào `DSNV_XOA.txt` |
| 8 | Thêm nhân viên | Thêm nhân viên mới, lưu vào `DSNV_THEM.txt` |
| 9 | Sửa thông tin nhân viên | Cập nhật thông tin nhân viên hiện có, lưu vào `DSNV_SUA.txt` |

## 📁 Cấu Trúc Dữ Liệu

### Cấu Trúc Employee
```cpp
struct Employee {
    string EmployeeID;      // Mã nhân viên
    string Name;            // Tên nhân viên
    string DoB;             // Ngày sinh
    string Email;           // Email
    string Address;         // Địa chỉ
    int SoNgayCong;         // Số ngày công
    double LuongNgay;       // Lương theo ngày
    double ThucLinh;        // Lương thực lĩnh (SoNgayCong * LuongNgay)
};
```

### Danh Sách Liên Kết Đơn
```cpp
struct Node {
    Employee data;
    Node* pNext;
};
typedef Node* LIST;
```

## 🛠 Các Hàm Chính

### Quản lý danh sách
- `create_list(LIST& l)` - Tạo danh sách rỗng
- `create_node(Employee emp)` - Tạo node mới
- `add_head(LIST& l, Employee emp)` - Thêm vào đầu danh sách
- `add_tail(LIST& l, Employee emp)` - Thêm vào cuối danh sách
- `add_pos(LIST& l, Employee emp, int pos)` - Thêm tại vị trí chỉ định
- `len_list(LIST l)` - Tính độ dài danh sách

### Nhập/Xuất dữ liệu
- `input_list(LIST& l)` - Nhập danh sách từ bàn phím
- `output_list(LIST l)` - Hiển thị danh sách
- `output_employee(Employee emp)` - Hiển thị thông tin một nhân viên
- `read_file(string filename, fstream& f, LIST& l)` - Đọc từ file
- `write_file(string filename, fstream& f, LIST l)` - Ghi vào file

### Tìm kiếm
- `check_employee_id(LIST l, string id)` - Kiểm tra mã nhân viên tồn tại
- `search_by_id(LIST l)` - Tìm theo mã nhân viên
- `search_by_name(LIST l)` - Tìm theo tên nhân viên

### Xử lý dữ liệu
- `sort_by_salary(LIST& l)` - Sắp xếp theo lương giảm dần
- `display_lowestEmp(LIST l)` - Hiển thị nhân viên lương thấp nhất
- `add_emp(LIST& l)` - Thêm nhân viên mới
- `delete_emp(LIST& l)` - Xóa nhân viên
- `update_emp(LIST& l)` - Sửa thông tin nhân viên

## 📂 Cấu Trúc File

```
├── main.cpp                 # Mã nguồn chính
├── README.md               # Tệp hướng dẫn này
├── DSNV.txt                # Dữ liệu nhân viên gốc
├── DSNV_SAPXEP.txt        # Danh sách sau khi sắp xếp
├── DSNV_THEM.txt          # Danh sách nhân viên vừa thêm
├── DSNV_SUA.txt           # Thông tin nhân viên vừa sửa
└── DSNV_XOA.txt           # Thông tin nhân viên vừa xóa
```

## 🚀 Cách Sử Dụng

### 1. Compile chương trình
```bash
g++ main.cpp -o qlnv
```

### 2. Chạy chương trình
```bash
./qlnv
```
hoặc trên Windows:
```bash
qlnv.exe
```

### 3. Sử dụng menu
Chương trình sẽ hiển thị menu với các lựa chọn:
```
        CHUONG TRINH QUAN LY NHAN VIEN
========================================
1. Nhap danh sach nhan vien
2. Doc danh sach nhan vien tu file
3. Tim kiem theo ma nhan vien
4. Tim kiem theo ten nhan vien
5. Xuat nhan vien co luong thap nhat
6. Sap xep theo luong (giam dan)
7. Xoa nhan vien
8. Them nhan vien
9. Sua thong tin nhan vien
0. Thoat chuong trinh
```

Nhập số (0-9) để chọn tác vụ muốn thực hiện.

## 📝 Định Dạng File Dữ Liệu

Mỗi nhân viên được lưu trên 8 dòng liên tiếp:

```
MaNhanVien
TenNhanVien
NgaySinh
Email
DiaChi
SoNgayCong
LuongNgay
ThuLinh
```

**Ví dụ:**
```
NV001
Nguyen Van A
01/01/1990
nguyen.a@company.com
123 Nguyen Hue, Ho Chi Minh
22
250000
5500000
```

## 💡 Lưu Ý Quan Trọng

1. **Kiểm tra mã trùng**: Chương trình không cho phép thêm nhân viên có mã trùng với dữ liệu hiện có
2. **Lưu file tự động**: Khi chọn tác vụ (thêm, xóa, sửa), dữ liệu sẽ tự động lưu vào các file tương ứng
3. **File DSNV.txt**: Luôn được cập nhật khi thoát chương trình
4. **Định dạng ngày**: Sử dụng định dạng DD/MM/YYYY
5. **Lương thực lĩnh**: Tự động tính từ Số ngày công × Lương ngày

## ⚙️ Yêu Cầu Hệ Thống

- **Compiler**: GCC, Clang hoặc MSVC
- **C++ Standard**: C++11 trở lên
- **Hệ điều hành**: Windows, Linux, macOS

## 📚 Khái Niệm DSA Sử Dụng

- **Danh sách liên kết đơn (Singly Linked List)**: Cấu trúc dữ liệu chính
- **Sắp xếp (Sorting)**: Bubble sort để sắp xếp theo lương
- **Tìm kiếm (Searching)**: Linear search cho tìm kiếm tuyến tính
- **File I/O**: Đọc/ghi file dữ liệu

## � Cấu Trúc Dữ Liệu & Giải Thuật Chi Tiết

### 1. Danh Sách Liên Kết Đơn (Singly Linked List)
**Mô tả**: Cấu trúc dữ liệu lưu trữ danh sách nhân viên với các node được liên kết bằng con trỏ.

**Ưu điểm**:
- Thêm/xóa phần tử tại đầu hoặc cuối danh sách nhanh chóng
- Động cấp phát bộ nhớ, không cần kích thước cố định

**Nhược điểm**:
- Truy cập phần tử tại vị trí bất kỳ chậm (phải duyệt từ đầu)
- Sử dụng bộ nhớ cho con trỏ trong mỗi node

### 2. Sắp Xếp Bubble Sort
**Mô tả**: Sắp xếp danh sách nhân viên theo lương giảm dần bằng cách so sánh từng cặp phần tử liền kề.

**Quy trình**:
1. Duyệt danh sách từ đầu
2. So sánh từng cặp node liền kề
3. Nếu lương không đúng thứ tự, hoán đổi dữ liệu
4. Lặp lại cho đến khi danh sách được sắp xếp

### 3. Tìm Kiếm Tuyến Tính (Linear Search)
**Mô tả**: Tìm kiếm nhân viên bằng cách duyệt từng node từ đầu danh sách cho đến khi tìm thấy hoặc hết danh sách.

**Áp dụng**:
- Tìm kiếm theo mã nhân viên
- Tìm kiếm theo tên nhân viên (sử dụng `string::find()`)
- Kiểm tra mã trùng lặp

## ⏱️ Độ Phức Tạp Thuật Toán

| Hàm | Độ Phức Tạp Thời Gian | Độ Phức Tạp Không Gian | Ghi Chú |
|-----|----------------------|----------------------|---------|
| `create_list()` | O(1) | O(1) | Khởi tạo danh sách rỗng |
| `create_node()` | O(1) | O(1) | Tạo một node mới |
| `add_head()` | O(1) | O(1) | Thêm vào đầu danh sách |
| `add_tail()` | O(n) | O(1) | Phải duyệt để tìm cuối danh sách |
| `add_pos()` | O(n) | O(1) | Phải duyệt đến vị trí chỉ định |
| `len_list()` | O(n) | O(1) | Phải duyệt toàn bộ danh sách |
| `search_by_id()` | O(n) | O(1) | Tìm kiếm tuyến tính |
| `search_by_name()` | O(n) | O(k) | k = số kết quả tìm thấy |
| `sort_by_salary()` | O(n²) | O(1) | Bubble sort |
| `delete_emp()` | O(n) | O(1) | Phải tìm trước khi xóa |
| `add_emp()` | O(n) | O(1) | Kiểm tra trùng + thêm |
| `update_emp()` | O(n) | O(1) | Phải tìm trước khi sửa |
| `output_list()` | O(n) | O(1) | Duyệt và hiển thị |
| `read_file()` | O(n) | O(n) | Đọc n nhân viên từ file |
| `write_file()` | O(n) | O(1) | Ghi n nhân viên vào file |

**Ghi thích**: n = số lượng nhân viên trong danh sách

## 📋 Danh Sách Use Cases

### 1. Quản Lý Cơ Bản Nhân Viên
- **Use Case 1.1**: Thêm nhân viên mới
  - Actor: Quản lý HR
  - Precondition: Chương trình đã chạy, danh sách đã được tải
  - Main Flow: Chọn "8. Thêm nhân viên" → Nhập thông tin → Lưu vào DSNV_THEM.txt
  - Exception: Mã nhân viên trùng lặp

- **Use Case 1.2**: Xóa nhân viên
  - Actor: Quản lý HR
  - Main Flow: Chọn "7. Xóa nhân viên" → Nhập mã nhân viên → Xác nhận xóa → Lưu vào DSNV_XOA.txt

- **Use Case 1.3**: Cập nhật thông tin nhân viên
  - Actor: Quản lý HR
  - Main Flow: Chọn "9. Sửa thông tin nhân viên" → Nhập mã nhân viên → Cập nhật thông tin → Lưu vào DSNV_SUA.txt

### 2. Tìm Kiếm & Truy Vấn
- **Use Case 2.1**: Tìm kiếm nhân viên theo mã
  - Actor: Nhân viên HR, Quản lý
  - Main Flow: Chọn "3. Tìm kiếm theo mã nhân viên" → Nhập mã → Hiển thị thông tin

- **Use Case 2.2**: Tìm kiếm nhân viên theo tên
  - Actor: Nhân viên HR, Quản lý
  - Main Flow: Chọn "4. Tìm kiếm theo tên nhân viên" → Nhập tên (hoặc phần tên) → Hiển thị danh sách kết quả

- **Use Case 2.3**: Xem nhân viên có lương thấp nhất
  - Actor: Quản lý, Giám đốc
  - Main Flow: Chọn "5. Xem nhân viên có lương thấp nhất" → Hiển thị thông tin nhân viên

### 3. Báo Cáo & Phân Tích
- **Use Case 3.1**: Sắp xếp nhân viên theo lương
  - Actor: Quản lý, Giám đốc
  - Main Flow: Chọn "6. Sắp xếp theo lương (giảm dần)" → Danh sách sắp xếp → Lưu vào DSNV_SAPXEP.txt

- **Use Case 3.2**: Xuất danh sách tất cả nhân viên
  - Actor: Nhân viên HR, Quản lý
  - Main Flow: Chọn "2. Đọc danh sách nhân viên từ file" → Hiển thị tất cả thông tin

### 4. Quản Lý Dữ Liệu
- **Use Case 4.1**: Nhập danh sách nhân viên từ bàn phím
  - Actor: Nhân viên HR
  - Main Flow: Chọn "1. Nhập danh sách nhân viên" → Nhập số lượng → Nhập từng nhân viên → Lưu vào DSNV.txt

- **Use Case 4.2**: Đọc dữ liệu từ file lúc khởi động
  - Actor: Hệ thống
  - Precondition: File DSNV.txt tồn tại
  - Main Flow: Chương trình chạy → Tự động đọc DSNV.txt → Nạp dữ liệu vào danh sách

- **Use Case 4.3**: Lưu dữ liệu khi thoát chương trình
  - Actor: Hệ thống
  - Precondition: Chương trình kết thúc (chọn "0. Thoát")
  - Main Flow: Ghi toàn bộ danh sách vào DSNV.txt → Thoát chương trình

## �👨‍💻 Tác Giả

Chương trình này được tạo cho mục đích học tập về cấu trúc dữ liệu và giải thuật.