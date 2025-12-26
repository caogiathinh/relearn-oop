Chắc chắn rồi, đây là phiên bản đã được loại bỏ các thẻ \`\`.

# Quy tắc viết code - Coding Conventions

**Ver. 25.10**

-----

## Tên app/project

Tên dành cho toàn bộ dự án phần mềm của bạn.

  * **Quy ước**: Danh từ, chữ hoa từng đầu từ (PascalCase), trừ tình huống đặc biệt về nhận dạng thương hiệu (iCloud).
  * Không dùng khoảng trắng, dấu tiếng Việt, và các kí tự đặc biệt.
  * **Ví dụ**: `StudentManagement`, `HelloWorld`, `PetCareSystem`, `FacebookMessenger`, `OnlineBookstore`, `MusicPlayerApp`, `TaskManagementSystem`.

-----

## Tên package/thư mục chứa code

Các gói (packages) dùng để tổ chức code của bạn thành các nhóm logic, giống như các thư mục cho tệp tin.

  * **Quy ước**: Danh từ, chữ thường, cố gắng dùng từ đơn. Các thư mục con phân cách nhau bởi dấu chấm.
  * Theo lẽ thường, package gốc dùng phần đuôi của tên miền của tổ chức (ví dụ `com`, `edu`, `gov`).
  * Không dùng khoảng trắng, dấu tiếng Việt, và các kí tự đặc biệt.
  * **Ví dụ**: `com.apple.quicktime`, `util`, `data`, `org.hibernate.validator`, `vn.edu.fpt.se.controller`, `vn.edu.fpt.se.model`.

-----

## Tên class/interface

Class là bản thiết kế cho các đối tượng. Interface là một bản hợp đồng về các hành vi mà một class phải thực hiện.

  * **Quy ước**: Danh từ, chữ hoa từng đầu từ (PascalCase). Viết cả từ, tránh viết tắt.
  * **Ví dụ**: `Dog`, `Cat`, `Student`, `FileInputStream`, `Vehicle`, `Customer`, `HttpRequest`, `DatabaseConnection`, `NhanVien`, `HoaDon`.

-----

## Tên biến và hằng số

Biến lưu trữ dữ liệu có thể thay đổi, trong khi hằng số lưu trữ dữ liệu không đổi.

  * **Quy ước biến thường**: Danh từ, chữ hoa từng đầu từ, từ đầu tiên viết chữ thường (cú pháp con lạc đà, camelCase).

      * Nên đặt tên biến có ý nghĩa, tránh viết tắt trừ những biến tạm thời (`t`, `tmp`, `i`, `j`, `k`).
      * **Ví dụ**: `luongCoBan`, `yearOfBirth`, `yob`, `firstName`, `productPrice`, `numberOfStudents`.

  * **Quy ước hằng số (const, final)**: Danh từ, chữ hoa tất cả các từ, dùng gạch dưới để kết nối các từ.

      * **Ví dụ**: `VAT`, `MAX_SPEED`, `PI`, `DEFAULT_TIMEOUT`, `INTEREST_RATE`, `MAX_LOGIN_ATTEMPTS`.

-----

## Tên function/method/hàm

Hàm (function) hoặc phương thức (method) định nghĩa một hành động hoặc một phép tính toán.

  * **Quy ước**: Động từ kèm theo bổ ngữ (`Verb + Object`), theo cú pháp con lạc đà (camelCase).
  * **Khuyến khích**: Có ghi chú cho tên hàm (ý nghĩa, đầu vào, đầu ra...).
  * **Ví dụ**: `tinhLuong()`, `computeArea()`, `sortByName()`, `calculateTotalPrice()`, `validateUserInput()`, `getUserById()`, `printInvoice()`.

-----

## Các quy ước khác

### Indentation/gióng lề cho code

  * **Quy ước**: Mặc định các đoạn code mức con sẽ thụt vào so với mức cha 4 khoảng trắng (tương đương 1 phím tab).
  * **Ví dụ**:
    ```java
    public void printGrade(double score) {
        if (score >= 5.0) {
            System.out.println("Passed!");
            if (score >= 8.0) {
                System.out.println("Good job!");
            }
        } else {
            System.out.println("Failed!");
        }
    }
    ```

### Tránh hard-code

  * **Quy ước**: Các giá trị, con số có ý nghĩa riêng trong code, phải được định nghĩa thành hằng số.
  * **Ví dụ**:
      * **Không nên**:
        ```java
        // "1.1" là một "magic number", không rõ ý nghĩa
        double finalPrice = initialPrice * 1.1;
        ```
      * **Nên làm**:
        ```java
        final double VALUE_ADDED_TAX = 0.1;
        double finalPrice = initialPrice * (1 + VALUE_ADDED_TAX);
        ```

### Kiểm thử và Tái sử dụng

  * **Tư duy tách hàm và tái sử dụng (re-use)**: Tránh lặp lại các khối lệnh, thay vào đó viết một hàm để dùng lại.
  * **Chặn dữ liệu nhập (Validation)**: Mọi giá trị nhập từ bàn phím phải được kiểm tra để chặn các lỗi không mong muốn.
  * **Tránh sụp đổ chương trình (crash)**: Kiểm tra kĩ các ngoại lệ (exception), tràn biên, sai định dạng, null pointer....

-----

## Cấu trúc chương trình (trong C)

  * Các hàm phải có **prototype** (dòng tiêu đề khai báo hàm) đặt ở đầu file, dưới các lệnh `#include` và `#define`.
  * **Cấu trúc file `main.c` mẫu**:
    ```c
    // #include statements
    #include <stdio.h>
    #include <stdlib.h>

    // #define statements
    #define PI 3.14

    // type definitions
    const float VAT = 0.1;

    // prototypes
    void sayHello(char* message);

    // the main function
    int main() {
        sayHello("Welcome to the C World!"); // invoke the function
        return 0;
    }

    // the body of the functions
    void sayHello(char* message) {
        printf("%s\n", message);
    }
    ```