# WatchStore FE

Frontend cho website ban dong ho WatchStore, xay dung bang React, TypeScript va Vite. Ung dung phuc vu khach hang, nhan vien va chu cua hang voi cac luong mua hang, quan ly san pham, don hang, bao hanh, nha cung cap va bao cao.

## Tinh nang chinh

- Trang public: trang chu, danh sach san pham, tim kiem, chi tiet san pham, so sanh san pham, gioi thieu va chinh sach.
- Tai khoan khach hang: dang ky, xac thuc email OTP, dang nhap, quen mat khau, ho so, thong bao.
- Mua hang: gio hang, dat hang, lich su don hang, huy don, danh gia san pham va yeu cau bao hanh.
- Khu vuc Staff: dashboard, xu ly don hang, bao hanh, san pham, danh muc, khach hang va ho tro.
- Khu vuc Owner: quan ly san pham, danh muc, nha cung cap, phieu nhap, voucher, staff, khach hang, bao hanh, noi dung va bao cao.
- Tich hop API backend qua Axios, React Query va co che gan JWT vao request.
- Co mock data va test cho auth, cart, route guard va AI adapter.

## Cong nghe

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

## Cau truc thu muc

```text
frontend/
  src/
    app/              # router, layout, provider
    api/              # axios client dung chung
    assets/           # style toan cuc
    entities/         # type theo domain
    features/         # module theo man hinh/chuc nang
    mocks/            # du lieu mock
    services/         # service goi API va adapter
    shared/           # UI, hook, constant, util dung chung
```

## Yeu cau moi truong

- Node.js 20 tro len
- npm
- Backend WatchStore dang chay mac dinh tai `http://localhost:8080/api`

## Cai dat va chay local

```bash
cd frontend
npm install
npm run dev
```

Ung dung Vite mac dinh chay tai `http://localhost:5173`.

## Cau hinh bien moi truong

Tao file `.env` trong thu muc `frontend/` neu can doi base URL backend:

```env
VITE_API_BASE_URL=http://localhost:8080/api
```

Ma nguon cung ho tro ten bien cu:

```env
VITE_API_URL=http://localhost:8080/api
```

Neu khong khai bao bien moi truong, frontend se dung `http://localhost:8080/api`.

## Lenh huu ich

```bash
npm run dev            # chay development server
npm run build          # type-check va build production
npm run preview        # xem ban build production
npm run lint           # kiem tra ESLint
npm run format         # format code bang Prettier
npm run test           # chay Vitest watch mode
npm run test:run       # chay test mot lan
npm run test:coverage  # chay test kem coverage
```

## Ket noi backend

Frontend goi API qua `src/api/axiosClient.ts`. Client tu dong:

- dung `VITE_API_BASE_URL` hoac `VITE_API_URL` lam base URL;
- them header `Authorization: Bearer <token>` neu da dang nhap;
- xoa token va dieu huong ve trang dang nhap khi gap loi `401` ngoai request login.

Repo backend tuong ung: <https://github.com/truonggiang205/WatchStore>

## Ghi chu phat trien

- Code chia theo feature de de mo rong module moi.
- Cac route co phan quyen duoc bao boi `RouteGuard`.
- Cac service trong `src/services/api` mapping du lieu backend sang type frontend.
- Thu muc `docs/` luu ghi chu thay doi va playbook cho cac module lon.
