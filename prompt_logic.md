# HỒ SƠ PHÂN TÍCH LOGIC PROMPT & TƯ DUY UX
**Dự án:** WoodERP — ERP sản xuất đồ nội thất
**Nhóm:** 15 (1 thành viên) · **Học phần:** Thiết kế Web (111101)

---

## 1. Prompt điều chỉnh cubic-bezier (yêu cầu mục B – Tuần 5)

> *"Đóng vai chuyên gia Motion Design. Thay toàn bộ `ease`/`linear` mặc định bằng:
> 1. `--ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1)` cho hover card, nút bấm, modal, thẻ lật 3D (cảm giác đàn hồi).
> 2. `--ease-smooth: cubic-bezier(0.4, 0, 0.2, 1)` cho fade-in, menu mở rộng (dừng êm).
> 3. Không animation bằng `top/left/margin`; chỉ dùng `transform` và `opacity` để chạy trên GPU."*

## 2. Prompt xử lý lỗi (Debug & Refactor)

| Vấn đề | Prompt xử lý | Kết quả |
| :-- | :-- | :-- |
| Hover card giật do đổi `margin-top` gây reflow | "Thay `margin-top` bằng `transform: translateY(-6px)` và thêm `will-change: transform`." | Mượt 60fps |
| Thẻ lật 3D lộ mặt sau | "Thêm `perspective` ở cha, `transform-style: preserve-3d` cho khung lật, `backface-visibility: hidden` cho hai mặt, mặt sau xoay sẵn `rotateY(180deg)`." | Lật đúng |
| Hai nhóm lọc (xưởng/trạng thái) xung đột | "Dùng hai nhóm radio khác `name`, mỗi quy tắc `:has(:checked)` chỉ ẩn thẻ không khớp nhóm của nó." | Lọc kết hợp (AND) |
| Typing effect đổi `width` gây reflow | "Dùng `clip-path: inset()` với `steps()` thay vì animate `width`." | Không reflow |

## 3. Lý do chọn hiệu ứng theo section (UX)

| Section | Hiệu ứng | Lý do |
| :-- | :-- | :-- |
| Hero | `fadeInUp`, typing, chấm nhịp đập | Dẫn mắt người dùng vào thông điệp chính, gợi cảm giác hệ thống đang chạy thực |
| Thẻ phân hệ / lệnh SX | Hover nhấc 6px, xoay icon, xuất hiện so le | Phản hồi rằng thẻ bấm được; nhịp điệu thị giác dễ chịu |
| Thanh tiến độ & tồn kho | `scaleX` từ 0 → giá trị thật | Người quản lý nhìn nhanh mức hoàn thành; màu đỏ-cam cho vật tư thấp |
| Chip bộ lọc | `translateX(4px)`, đổi màu khi chọn | Luôn biết mình đang lọc theo gì |
| Thẻ lật 3D | Lật 180° | Gom thông tin phụ ở mặt sau, không làm vỡ bố cục |
| Modal chi tiết | Scale + blur nền | Tập trung vào một lệnh sản xuất |
| Banner parallax | `background-attachment: fixed` | Tạo chiều sâu, ngăn cách vùng nội dung |
| FAB | `pulseGlow`, nằm góc phải dưới | Hành động chính (tạo lệnh) trong tầm ngón cái (định luật Fitts) |

## 4. Hiệu năng & Accessibility
- Animation chỉ dùng `transform`/`opacity` → chạy ở tầng composite, mượt 60fps.
- Có skip-link, `aria-label`, `aria-current`, `:focus-visible`, `prefers-reduced-motion`.
- **Zero JavaScript:** không phụ thuộc script, tải nhanh, không lỗi do chặn JS.
