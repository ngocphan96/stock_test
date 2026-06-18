# Hướng dẫn đưa demo lên GitHub & hoàn chỉnh — từng bước

Tài liệu này đi từ thư mục `radar-demo/` trên máy bạn → một link công khai gửi được cho khách. Làm theo thứ tự A → H.

---

## A. Kiến trúc thư mục (repo)

Toàn bộ file nằm **phẳng ở thư mục gốc** của repo (GitHub Pages mặc định chạy `index.html` ở gốc):

```
radar-demo/                  ← thư mục gốc repo
│
├── index.html               ← Landing — TRANG VÀO mặc định của Pages
├── menu.html                ← Điều hướng tới tất cả màn (gửi link này khi demo)
│
├── onboarding.html          ┐
├── radar.html               │
├── detail.html              ├─ Luồng lõi
├── zalo.html                ┘
│
├── ngay-binh-thuong.html    ┐
├── track-record.html        ├─ Niềm tin & giữ chân
├── canh-bao.html            ┘
│
├── bang-gia.html            ┐
├── nganh.html               │
├── ro-tiem-nang.html        ├─ Test sẵn lòng trả tiền
├── bao-cao-tuan.html        ┘
│
├── cai-dat.html             ← Cá nhân hóa
│
├── 404.html                 ← Trang báo lỗi (Pages tự dùng khi sai link)
├── favicon.svg              ← Biểu tượng tab trình duyệt
├── robots.txt               ← Chặn Google lập chỉ mục (demo riêng)
├── .gitignore               ← Bỏ qua file rác khi commit
├── README.md                ← Mô tả repo (hiện ở trang chủ GitHub)
└── HUONG-DAN.md             ← File này
```

**Mỗi `.html` là tự chứa** (CSS/JS nằm trong file), liên kết bằng đường dẫn tương đối → chạy tốt trên Pages, không lo lệch đường dẫn.

### Vai trò các file phụ trợ

| File | Để làm gì | Có cần sửa không |
|---|---|---|
| `index.html` | Trang vào mặc định | **Có** — nối Formspree (mục G) |
| `404.html` | Hiện khi khách vào sai link, có nút quay lại | Không |
| `favicon.svg` | Logo ◉ trên tab trình duyệt | Không |
| `robots.txt` | Yêu cầu công cụ tìm kiếm **không** lập chỉ mục | Không |
| `.gitignore` | Tránh đưa file rác (`.DS_Store`…) lên repo | Không |
| `README.md` | Mô tả + dán link demo sau khi có | Nên dán link |

---

## B. Chuẩn bị

1. Có tài khoản **GitHub** (miễn phí) tại github.com.
2. Có sẵn thư mục `radar-demo/` với toàn bộ file ở trên trên máy.
3. Chọn **một** trong hai cách đưa lên: **Cách 1 (web, dễ nhất)** hoặc **Cách 2 (Git CLI)**.

---

## C. Cách 1 — Upload qua web (khuyến nghị, không cần cài gì)

1. Vào github.com → góc phải trên bấm **+** → **New repository**.
2. **Repository name:** `radar-demo` (hoặc tên khó đoán hơn cho kín đáo, vd `rd-demo-7k2`).
3. Chọn **Public** (Pages bản free cần Public). Bỏ qua các ô còn lại → **Create repository**.
4. Ở trang repo trống, bấm **uploading an existing file** (dòng chữ xanh giữa trang).
5. Mở thư mục `radar-demo` trên máy, **chọn tất cả file** (Ctrl/Cmd+A) rồi **kéo–thả** vào khung upload.
   - Lưu ý: kéo **các file**, không kéo cả thư mục cha. File `.gitignore` có thể bị ẩn — bật "hiện file ẩn" nếu cần (không có cũng không sao).
6. Cuộn xuống, bấm **Commit changes**.

→ Sang **mục E** để bật Pages.

---

## D. Cách 2 — Upload qua Git (nếu bạn quen dòng lệnh)

```bash
# tại thư mục radar-demo trên máy
git init
git add .
git commit -m "Radar danh mục - demo"
git branch -M main
# tạo repo trống tên radar-demo trên GitHub trước, rồi:
git remote add origin https://github.com/<tên-github>/radar-demo.git
git push -u origin main
```

→ Sang **mục E**.

---

## E. Bật GitHub Pages

1. Trong repo → tab **Settings**.
2. Menu trái → **Pages**.
3. Mục **Build and deployment**:
   - **Source:** *Deploy from a branch*
   - **Branch:** `main` · thư mục `/ (root)` → **Save**.
4. Đợi ~1–2 phút. Tải lại trang Pages, sẽ hiện dòng:
   **"Your site is live at https://<tên-github>.github.io/radar-demo/"**

Đó là link công khai của bạn.

---

## F. Lấy link & kiểm tra

Mở thử và bấm dạo:

| Việc kiểm tra | Đường dẫn |
|---|---|
| Trang giới thiệu | `…/radar-demo/` |
| Menu tất cả màn | `…/radar-demo/menu.html` |
| Bấm qua lại giữa các màn | từ Landing → Radar → chi tiết → … |

Checklist nhanh: ✅ trang mở được, ✅ favicon ◉ hiện trên tab, ✅ các nút chuyển màn chạy, ✅ vào link sai (vd `…/abc.html`) thấy trang 404 có nút quay lại.

> **Gửi khách:** thường gửi `…/radar-demo/menu.html` để khách tự dạo, hoặc `…/radar-demo/` nếu muốn họ vào từ trang giới thiệu.

---

## G. Nối form "Đăng ký quan tâm" (để thu được liên hệ thật)

Trang tĩnh không có server, nên dùng dịch vụ form miễn phí **Formspree**.

1. Vào **formspree.io** → đăng ký → **New form** → đặt tên (vd "Radar leads").
2. Copy **endpoint** của form, dạng: `https://formspree.io/f/abcdwxyz`.
3. Trong repo, mở **`index.html`** → bấm biểu tượng ✏️ (Edit) → tìm dòng:
   ```html
   <form id="lead" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
4. Thay `YOUR_FORM_ID` (hoặc cả URL) bằng endpoint của bạn → **Commit changes**.
5. Mở lại site, nhập thử số Zalo/email và gửi → kiểm tra email Formspree báo về.

> Khi chưa nối, form vẫn hiện "Cảm ơn" để demo trôi chảy, **nhưng không lưu** liên hệ. Có thể thay bằng Google Forms/Tally nếu muốn.

---

## H. Quyền riêng tư & các tuỳ chọn

- **Không lên Google:** đã có `robots.txt` chặn lập chỉ mục. Muốn kín hơn nữa, đặt **tên repo khó đoán** và chỉ gửi link cho người cần.
- **Gắn tên miền riêng (tuỳ chọn):** nếu đã có domain (vd từ phần đặt tên trước), trong **Settings → Pages → Custom domain** nhập tên miền, rồi tạo bản ghi DNS `CNAME` trỏ về `<tên-github>.github.io`. GitHub sẽ tự cấp HTTPS.
- **Cập nhật về sau:** sửa file ngay trên GitHub (✏️ Edit → Commit) hoặc `git push` lại. Pages tự build lại sau ~1 phút.

---

## Checklist hoàn chỉnh

- [ ] Tạo repo `radar-demo` (Public)
- [ ] Upload toàn bộ file (Cách 1 hoặc 2)
- [ ] Settings → Pages → Branch `main` /root → Save
- [ ] Có link `github.io` và mở được
- [ ] Kiểm tra favicon + chuyển màn + trang 404
- [ ] Nối Formspree trong `index.html` và gửi thử
- [ ] Dán link demo vào `README.md`
- [ ] Gửi `…/menu.html` cho 5–10 khách + ghi nhận phản hồi
```
