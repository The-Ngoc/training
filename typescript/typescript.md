1. TS Simple Types & Explicit / InferenceBa
    3 Kiểu dữ liệu nguyên thủy phổ biến nhất là string, number và boolean. 
    Có 2 cách khai báo:
        Explicit (Tường minh): Chỉ định trực tiếp kiểu dữ liệu bằng dấu ':'
        Inference (Suy luận kiểu): TypeScript tự động nhận diện kiểu dữ liệu dựa trên giá trị khởi tạo ban đầu.
 
    let firstName: string = "Ngọc"; // Explicit
    let age = 21;                   // Inference 


2. TS Special Types
    Các kiểu dữ liệu đặc biệt:

    void: Dùng khi hàm không trả về giá trị nào.
    any: Tắt tính năng kiểm tra kiểu.
    unknown: Tương tự any nhưng bắt buộc phải kiểm tra kiểu trước khi thao tác hoặc gọi phương thức trên biến đó.
    never: Biểu thị giá trị không bao giờ xảy ra (ví dụ: hàm luôn ném ra lỗi throw Error).
    undefined & null: Tương ứng với các kiểu dữ liệu rỗng trong JavaScript.
    
3. TS Arrays
    Định nghĩa kiểu cho các phần tử trong mảng và hỗ trợ từ khóa readonly để ngăn mảng bị thay đổi:
    const names: string[] = ["An", "Thắng"];
    const scores: readonly number[] = [9, 10];  // Không thể .push() hay sửa phần tử

4. TS Object Types
    Mô tả cấu trúc các thuộc tính bên trong một đối tượng, hỗ trợ thuộc tính tùy chọn (Optional property) với dấu ?:
    const user: { name: string; age?: number } = {
        name: "Ngọc" // Không bắt buộc phải truyền age
    };

5. TS Aliases & Interfaces
    Cho phép đặt tên riêng cho kiểu dữ liệu để tái sử dụng nhiều lần:
    Type Alias (type): Dùng được cho mọi kiểu dữ liệu (nguyên thủy, union, tuple, object).
    Interface (interface): Chỉ dùng cho kiểu Object, hỗ trợ kế thừa (extends) rất trực quan.

    type UserID = string | number;

    interface User {
        id: UserID;
        username: string;
    }

    interface Admin extends User {
        role: string;
    }

6. TS Union Types & Literal Types
    Union Types (|): Cho phép một biến nhận một trong nhiều kiểu dữ liệu khác nhau.
    Literal Types: Giới hạn biến chỉ được nhận các giá trị cụ thể (chuỗi, số hoặc boolean chính xác).   
    
    let code: string | number = 404; // Union Type
    type Status = "pending" | "success" | "failed"; // Literal Type kết hợp Union

7. TS Functions
    Định kiểu chặt chẽ cho tham số đầu vào và giá trị trả về của hàm:
    void: Dùng khi hàm không trả về giá trị nào.
    Hỗ trợ tham số tùy chọn (?), tham số mặc định (=) và Rest parameters (...).
    
    function sum(a: number, b: number, c: number = 0): number {
        return a + b + c;
    }

    function logMessage(msg: string): void {
        console.log(msg);
    }
    
8. TS Null (Null & Undefined)
    Khi bật chế độ strictNullChecks, bạn phải chủ động xử lý null và undefined: 
    Optional Chaining (?.): Truy cập thuộc tính an toàn mà không gây lỗi nếu đối tượng cha bị rỗng.
    Nullish Coalescing (??): Cung cấp giá trị dự phòng khi vế trái là null hoặc undefined.
    Non-null Assertion (!.): Khẳng định với trình biên dịch rằng giá trị chắc chắn không phải null/undefined.
9. TS Async Programming
    Khi làm việc với bất đồng bộ (async/await), hàm luôn trả về một Promise<T>, trong đó T là kiểu dữ liệu sau khi phân giải thành công: 
    
    async function fetchUser(id: number): Promise<{ id: number; name: string }> {
        return { id, name: "Ngọc" };
    }

10. TS with React & Node.js
    Với React: Định kiểu cho component Props, useState<T>(), và các sự kiện DOM như React.ChangeEvent<HTMLInputElement>, React.MouseEvent<HTMLButtonElement>.   
    Với Node.js (Express): Cài đặt @types/node, @types/express và sử dụng các kiểu Request, Response, NextFunction để xử lý route rõ ràng.   
    
11. TS Basic Generics
    Tạo ra các "biến kiểu dữ liệu" (thường ký hiệu là <T>) giúp viết hàm, interface hoặc class có thể hoạt động với nhiều kiểu dữ liệu khác nhau mà vẫn giữ nguyên tính an toàn kiểu: 
    
    function wrapInArray<T>(value: T): T[] {
        return [value];
    }

    const numArr = wrapInArray<number>(123);    // Trả về number[]
    const strArr = wrapInArray<string>("Hello"); // Trả về string[]
    
12. TS Utility Types
    Các kiểu dữ liệu tích hợp sẵn giúp biến đổi từ một kiểu Object ban đầu sang kiểu mới nhanh chóng mà không phải viết lại: 
    
    Utility TypeCông dụng chínhPartial<T>Biến tất cả các thuộc tính trong T thành tùy chọn (?).Required<T>Biến tất cả các thuộc tính trong T thành bắt buộc.Readonly<T>Không cho phép chỉnh sửa bất kỳ thuộc tính nào của T.Pick<T, 'a' 'b' |>Tạo kiểu mới bằng cách chỉ lấy ra các thuộc tính được chỉ định từ T.Omit<T, 'a'>Tạo kiểu mới bằng cách loại bỏ các thuộc tính được chỉ định khỏi T.Record<K, V>Định nghĩa một Object có kiểu của key là K và kiểu của value là V.
    
13. TS Type Guards
    Kỹ thuật kiểm tra để thu hẹp kiểu dữ liệu (Type Narrowing) trong một nhánh điều kiện if/else:typeof: Kiểm tra kiểu nguyên thủy (string, number, boolean).instanceof: Kiểm tra đối tượng thuộc về một Class cụ thể.in: Kiểm tra xem một thuộc tính có tồn tại trong Object hay không.Type Predicate (param is Type): Hàm kiểm tra kiểu tự định nghĩa. 
    
    function printId(id: string | number) {
    if (typeof id === "string") {
    console.log(id.toUpperCase()); // TS hiểu chắc chắn id là string ở đây
        }
    }

14. TS Casting (Ép kiểu)
    Dùng từ khóa as (hoặc <Type>) để ghi đè kiểu dữ liệu mà TypeScript suy luận. 
    Casting không thực sự chuyển đổi dữ liệu lúc chạy (runtime) mà chỉ báo cho trình biên dịch biết cách hiểu biến đó:

    let someValue: unknown = "Hello TypeScript";
    let strLength: number = (someValue as string).length;

15. TS Keyof & Index Signatures
    keyof: Trích xuất toàn bộ tên thuộc tính (key) của một Object thành một kiểu Union gồm các chuỗi.   
    Index Signatures: Dùng khi chưa biết trước tên các thuộc tính của Object nhưng biết rõ kiểu của key và value.   
    
    TypeScript
    
    interface Student { name: string; gpa: number; }
    type StudentKeys = keyof Student; // "name" | "gpa"

    interface StringMap {
        [key: string]: number; // Cho phép thêm bất kỳ key chuỗi nào có giá trị là number
   }
    

16. TS Configuration (tsconfig.json)
    Tệp cấu hình điều khiển cách trình biên dịch TypeScript hoạt động. Các thuộc tính quan trọng nhất bao gồm:
    "target": Phiên bản JavaScript đầu ra sau khi biên dịch (ví dụ: ES2022).
    "strict": true: Bật toàn bộ các quy tắc kiểm tra kiểu nghiêm ngặt.
    "outDir" & "rootDir": Thư mục chứa file JS sau khi build và thư mục chứa code TS gốc.


17. TS Definitely Typed
    Khi dùng các thư viện viết bằng JavaScript thuần (không có sẵn file định nghĩa kiểu .d.ts), cài đặt thêm gói khai báo kiểu từ kho lưu trữ cộng đồng DefinitelyTyped thông qua tiền tố @types/:Bash  
    
    npm install --save-dev @types/lodash @types/express


18. TS Enums
    Định nghĩa một tập hợp các hằng số có tên gọi rõ ràng, gồm Numeric Enums (mặc định tự tăng từ 0) và String Enums:
    TypeScript
    
    enum Role {
        Admin = "ADMIN",
        User = "USER",
        Guest = "GUEST"
    }           
    
    let currentRole: Role = Role.Admin;