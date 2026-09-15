# Sổ Quán Ăn Đã Lưu

Sổ tay cá nhân ghi lại các quán ăn/uống đã từng ghé hoặc muốn thử, kèm địa
chỉ, giờ mở cửa, số điện thoại và vài dòng nhận xét. Chạy hoàn toàn bằng
HTML/CSS/JS thuần, không cần build, không cần server hay database.

🔗 **Xem trực tiếp:** https://tranthaihoa-0409.github.io/so_tay_quan_an/

---

## Tính năng

- **Tìm kiếm** theo tên quán, loại quán, địa chỉ, ghi chú — không phân biệt
  dấu/hoa thường (gõ "com ga" vẫn ra "Cơm gà").
- **Lọc theo loại quán** bằng các tab phía trên bảng.
- **Sắp xếp** bằng cách nhấn vào tiêu đề cột (Quán / Loại / Chi nhánh); nhấn
  lại để đảo chiều tăng/giảm. Mặc định danh sách hiện theo **thứ tự thêm vào
  gần nhất lên trước**.
- **Nút 🎲 Ngẫu nhiên** — xáo trộn lại thứ tự hiển thị, hợp lúc phân vân
  không biết ăn gì.
- **Chỉ đường** — bấm biểu tượng 📍 cạnh mỗi địa chỉ để mở Google Maps chỉ
  đường trực tiếp từ vị trí hiện tại.
- Giao diện co giãn tốt trên điện thoại (bảng tự chuyển thành danh sách thẻ),
  hỗ trợ "Thêm vào màn hình chính" như một app (PWA).

## Cấu trúc file

| File                 | Vai trò                                                             |
|----------------------|----------------------------------------------------------------------|
| `data.js`            | **File duy nhất cần sửa** khi thêm/sửa quán — danh sách quán ăn.      |
| `index.html`         | Khung trang, tiêu đề cột, thanh tìm kiếm.                             |
| `app.js`             | Logic tìm kiếm/lọc/sắp xếp/hiển thị, không cần đụng khi thêm quán.    |
| `style.css`          | Giao diện (theme "sổ ghi chép"), màu badge theo từng loại quán.       |
| `manifest.json`      | Khai báo PWA (tên, icon, màu theme) để thêm vào màn hình chính.       |
| `dish.png` / `dish-maskable.png` | Icon app/favicon.                                          |

## Thêm quán mới

Chỉ cần sửa `data.js`, thêm 1 object vào mảng `DATA`:

```js
{
  name: "Tên quán",
  categories: ["Loại quán A"],   // có thể thêm nhiều loại: ["Loại A", "Loại B"]
  branches: [
    { label: "", address: "Địa chỉ", hours: "Giờ mở cửa", phone: "" }
    // thêm chi nhánh khác nếu có, mỗi chi nhánh 1 object trong mảng này
  ],
  note: "Ghi chú, món nổi bật, giá cả, không gian..."
}
```

Nếu loại quán đã có sẵn màu badge thì không cần sửa gì thêm. Nếu là loại
hoàn toàn mới, cần khai báo thêm màu ở `app.js` (`BADGE_MAP`) và `style.css`
(class `.badge-xxx`) — chi tiết đầy đủ và lịch sử các quyết định/bug đã gặp
khi làm dự án này nằm trong [`tong_hop_du_an.md`](tong_hop_du_an.md).

## Credit

Icon: [Dish icon — Pause08, Flaticon](https://www.flaticon.com/free-icon/dish_857718)
