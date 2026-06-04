# WatchStore FE

Frontend cho website bán đồng hồ WatchStore, xây dựng bằng React, TypeScript và Vite. Ứng dụng phục vụ khách hàng, nhân viên và chủ cửa hàng với các luồng mua hàng, quản lý sản phẩm, đơn hàng, bảo hành, nhà cung cấp và báo cáo.

## Tính năng chính

- Trang public: trang chủ, danh sách sản phẩm, tìm kiếm, chi tiết sản phẩm, so sánh sản phẩm, giới thiệu và chính sách.
- Tài khoản khách hàng: đăng ký, xác thực email OTP, đăng nhập, quên mật khẩu, hồ sơ, thông báo.
- Mua hàng: giỏ hàng, đặt hàng, lịch sử đơn hàng, hủy đơn, đánh giá sản phẩm và yêu cầu bảo hành.
- Khu vực Staff: dashboard, xử lý đơn hàng, bảo hành, sản phẩm, danh mục, khách hàng và hỗ trợ.
- Khu vực Owner: quản lý sản phẩm, danh mục, nhà cung cấp, phiếu nhập, voucher, staff, khách hàng, bảo hành, nội dung và báo cáo.
- Tích hợp API backend qua Axios, React Query và cơ chế gắn JWT vào request.
- Có mock data và test cho auth, cart, route guard và AI adapter.

## Công nghệ

- React 18
- TypeScript
- Vite
- Tailwind CSS
- React Router
- TanStack React Query
- Axios
- Zustand
- React Hook Form + Zod
- Radix UI, Lucide React, Recharts, Framer Motion
- Vitest + Testing Library

## Cấu trúc thư mục

```text
frontend/
  src/
    app/              # router, layout, provider
    api/              # axios client dùng chung
    assets/           # style toàn cục
    entities/         # type theo domain
    features/         # module theo màn hình/chức năng
    mocks/            # dữ liệu mock
    services/         # service gọi API và adapter
    shared/           # UI, hook, constant, util dùng chung
```

## Yêu cầu môi trường

- Node.js 20 trở lên
- npm
- Backend WatchStore đang chạy mặc định tại `http://localhost:8080/api`

## Cài đặt và chạy local

```bash
cd frontend
npm install
npm run dev
```

Ứng dụng Vite mặc định chạy tại `http://localhost:5173`.

## Cấu hình biến môi trường

Tạo file `.env` trong thư mục `frontend/` nếu cần đổi base URL backend:

```env
VITE_API_BASE_URL=http://localhost:8080/api
```

Mã nguồn cũng hỗ trợ tên biến cũ:

```env
VITE_API_URL=http://localhost:8080/api
```

Nếu không khai báo biến môi trường, frontend sẽ dùng `http://localhost:8080/api`.

## Lệnh hữu ích

```bash
npm run dev            # chạy development server
npm run build          # type-check và build production
npm run preview        # xem bản build production
npm run lint           # kiểm tra ESLint
npm run format         # format code bằng Prettier
npm run test           # chạy Vitest watch mode
npm run test:run       # chạy test một lần
npm run test:coverage  # chạy test kèm coverage
```

## Kết nối backend

Frontend gọi API qua `src/api/axiosClient.ts`. Client tự động:

- dùng `VITE_API_BASE_URL` hoặc `VITE_API_URL` làm base URL;
- thêm header `Authorization: Bearer <token>` nếu đã đăng nhập;
- xóa token và điều hướng về trang đăng nhập khi gặp lỗi `401` ngoài request login.

Repo backend tương ứng: <https://github.com/truonggiang205/WatchStore>

## Ghi chú phát triển

- Code chia theo feature để dễ mở rộng module mới.
- Các route có phân quyền được bao bởi `RouteGuard`.
- Các service trong `src/services/api` mapping dữ liệu backend sang type frontend.
- Thư mục `docs/` lưu ghi chú thay đổi và playbook cho các module lớn.
