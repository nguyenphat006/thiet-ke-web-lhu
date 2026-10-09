# WoodERP — Hệ thống ERP quản lý sản xuất đồ nội thất
**Học phần:** Thiết kế Web (111101)
**Nhóm:** 15 (1 thành viên) — Họ tên: _………_ · MSSV: _………_
**Công nghệ:** HTML5 + CSS3 thuần, **Zero JavaScript**, CSS Grid + Flexbox, Responsive Mobile-First

Demo (GitHub Pages): https://nguyenphat006.github.io/thiet-ke-web-lhu/

---

## Cấu trúc dự án

| File | Vai trò |
| :-- | :-- |
| `trangchu.html` | Tổng quan ERP: hero, phân hệ, quy trình 5 bước, tồn kho, đơn hàng |
| `sanxuat.html` | Lệnh sản xuất: bộ lọc xưởng/trạng thái, chế độ Lưới/Danh sách, modal, thẻ lật 3D |
| `style.css` | Design System (biến `:root`), layout, responsive, animation dùng chung |
| `prompt_logic.md` | Phân tích logic prompt & lý do chọn hiệu ứng (UX) |

## Bảng đối chiếu kiến thức Tuần 3 – 5

| Tuần | Nội dung | Triển khai |
| :-- | :-- | :-- |
| 3 | Semantic HTML, Grid, Flexbox | `<header> <nav> <main> <section> <aside> <article> <figure> <footer>`; layout 2 cột `280px 1fr`; lưới `repeat(auto-fit, minmax(250px,1fr))`; KPI/toolbar/card dùng Flex; khoảng cách bằng `gap`, không `float`/`table` |
| 4 | Design System, Responsive | Biến màu/spacing/font/shadow tại `:root`; Mobile-First với `min-width: 600px` và `1024px`; `meta viewport`; ảnh/svg `max-width:100%` |
| 5 | Animation & UX | FAB `pulseGlow` · thẻ lật 3D `preserve-3d` · typing effect · parallax `background-attachment: fixed` · hamburger → X · progress bar `scaleX` · `cubic-bezier` tùy chỉnh · chỉ dùng `transform`/`opacity` |

## Cách hoạt động của bộ lọc không dùng JS
Các `<input type="radio" class="ctrl">` đặt đầu `<body>`; `<label for>` là nút bấm. CSS dùng `body:has(#cat-go:checked) .lsx-card:not([data-cat="go"]) { display:none }`. Hai nhóm lọc (xưởng, trạng thái) độc lập nên tự kết hợp. Modal dùng `:target`, menu mobile dùng checkbox + `~`.

---

## 📝 NHẬT KÝ SỬ DỤNG PROMPT

### Lần 1 — Phân tích đề & dựng dự án

**Nguyên văn prompt:**
> "d:\Coder\Github\LHU\thiet-ke-web-lhu\HTKTLCN_PhamDangKhoa_NguyenDangNhat-main, xin chào giúp tôi đọc qua folder này để hiểu được họ đang làm bài tập về yêu cầu gì nhé, tôi cần bạn làm theo yêu cầu đề bài và copy lấy các cái file tài liệu liên quan chung còn về đề tài thì tôi muốn làm lien quan tới chủ đề hệ thống ERP sản xuất về đồ nội thất nhé và theo như tôi hiểu là sẽ sử dụng html css thuần kèm với các cái yêu cầu như là reponsive hay sử dụng grid flex box gì đấy thì làm giúp tôi nhé"

**Các bước kỹ thuật:**
1. Đọc bài mẫu → rút ra yêu cầu: tích hợp Tuần 3–5, không JS, có chú thích, có README nhật ký prompt và `prompt_logic.md`.
2. Giữ các file chung (`LICENSE`, `.vscode/settings.json`), đổi chủ đề sang ERP nội thất (xưởng gỗ, bọc nệm, sơn, lắp ráp; lệnh sản xuất, BOM, tồn kho).
3. Viết `style.css` (Design System) → `trangchu.html` → `sanxuat.html`.

### Lần 2 — Bổ sung thông tin nhóm

**Nguyên văn prompt:**
> "và nhóm tôi là 15 và chỉ có mình tôi là thành viên thôi nhé"

**Bước xử lý:** đổi thông tin nhóm thành Nhóm 15 (1 thành viên) ở README, footer, LICENSE.

### Lần 3 — Tổ chức thư mục

**Nguyên văn prompt:**
> "làm cho tôi trực tiếp ở folder thiet ke web lhu nhé ko tạo folder riêng"

**Bước xử lý:** chuyển toàn bộ file ra thư mục gốc `thiet-ke-web-lhu`, không dùng thư mục con.

### Lần 4 — Git & triển khai

**Nguyên văn prompt:**
> "https://github.com/nguyenphat006/thiet-ke-web-lhu.git xong thì giúp tôi connect vào cái repo này và xóa folder mình đang làm ví dụ kia đi nhé, xong thì tạo thêm 1 vài nhánh cơ bản kèm tách các commit để thấy được ta làm việc tách cho tôi thành 2 nhánh như là dev và staging và 1 nhánh main chính, sau đó giúp tôi deploy bằng github actions luôn"

**Bước xử lý:** kết nối remote, xóa thư mục mẫu, tách commit theo từng bước (design system → trang chủ → trang sản xuất → tài liệu → CI), tạo nhánh `dev` → `staging` → `main`, thêm workflow `.github/workflows/deploy.yml` deploy GitHub Pages khi push vào `main`.

---

## Quy trình nhánh
`dev` (phát triển) → `staging` (kiểm thử) → `main` (chính thức, tự động deploy).

## Kiểm thử
Mở `trangchu.html` bằng trình duyệt; bấm các chip lọc ở `sanxuat.html`; bấm "Xem nhanh" để mở modal; bấm `F12` thử ở kích thước điện thoại / tablet / laptop để kiểm tra responsive.
