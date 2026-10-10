# Thêm bài mới

Mỗi bài dài là một file HTML trong `articles/` (chỉ chứa phần nội dung: `<h2>`, `<p>`, `<table>`...,
không cần `<html>` hay `<body>`). Trang chỉ tải file đó khi người đọc mở bài.

## 3 bước

**1. Tạo file** `articles/ten-bai.html` (tên file = id của bài, viết thường, không dấu, dùng dấu gạch ngang).

**2. Khai báo bài** trong `index.html`, tìm `const ENTRIES = {` và thêm một mục:

```js
"ten-bai": {
  "kind": "law",
  "doc": "tt99",
  "crumb": ["Chế độ kế toán Thông tư 99"],
  "title": "Tiêu đề bài",
  "meta": "Dòng mô tả ngắn",
  "excerpt": "Khoảng 150–200 ký tự đầu của bài (dùng cho khung xem trước khi rê chuột)."
},
```

Nếu bài thuộc một tài liệu đã có, thêm id vào `toc` của tài liệu đó trong `const DOCS`
(ví dụ `articles: ["ten-bai"]`). Nếu là tài liệu mới, thêm một mục mới vào `DOCS`.

**3. Thêm vào sidebar trái** (1 dòng):

```html
<li><a href="#" data-id="ten-bai">Tên hiển thị</a></li>
```

Sau đó commit và push lên GitHub.

## Xem thử trên máy

Mở thẳng `index.html` sẽ không tải được bài (trình duyệt chặn). Chạy trong thư mục này:

```
python -m http.server 8000
```

rồi mở http://localhost:8000. Trên GitHub Pages thì chạy bình thường.

## Lưu ý

- Lần tìm kiếm đầu tiên sẽ tải toàn bộ bài một lần để tìm toàn văn (vài giây nếu bài rất nhiều).
- Mục lục sidebar 2 của TT 99 (`tt99`, `tt99-tk`) lọc trong hàm `buildSidebarToc`; `tt99-phuluc` dùng `CUSTOM_TOC`.
