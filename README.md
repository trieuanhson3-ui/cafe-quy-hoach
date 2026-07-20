# CAFE QUY HOẠCH — Website chính thức

> **Minh Bạch · Uy Tín · An Tâm**
> Tư vấn quy hoạch, pháp lý nhà đất, đền bù giải phóng mặt bằng và thiết kế xây dựng.

Đây là **toàn bộ mã nguồn** website chính thức của Cafe Quy Hoạch. Bạn sở hữu hoàn toàn bộ mã nguồn này. Website chạy độc lập, **không phụ thuộc vào bất kỳ nền tảng AI hay dịch vụ tạm thời nào** — chỉ cần HTML, CSS, JavaScript thuần, mở bằng trình duyệt là chạy.

---

## MỤC LỤC

1. [Chạy thử trên máy tính](#1-chạy-thử-trên-máy-tính)
2. [Cấu trúc dự án](#2-cấu-trúc-dự-án)
3. [Đưa mã nguồn lên GitHub](#3-đưa-mã-nguồn-lên-github)
4. [Deploy từ GitHub lên Netlify](#4-deploy-từ-github-lên-netlify)
5. [Cập nhật website sau này](#5-cập-nhật-website-sau-này)
6. [Những chỗ hay sửa nhất](#6-những-chỗ-hay-sửa-nhất)
7. [Quy tắc sao lưu (backup)](#7-quy-tắc-sao-lưu-backup)
8. [Nâng cấp AI Chat lên AI thật](#8-nâng-cấp-ai-chat-lên-ai-thật-tuỳ-chọn)
9. [Deploy lên Vercel](#9-deploy-lên-vercel-tuỳ-chọn)
10. [Xử lý sự cố thường gặp](#10-xử-lý-sự-cố-thường-gặp)

---

## 1. CHẠY THỬ TRÊN MÁY TÍNH

Giải nén thư mục, nhấp đúp vào file **`index.html`**. Website mở ngay trong trình duyệt, đầy đủ chức năng — không cần cài đặt gì.

---

## 2. CẤU TRÚC DỰ ÁN

```
cafe-quy-hoach/
├── index.html          ← Trang chính (nội dung hiển thị)
├── css/
│   └── style.css       ← Toàn bộ màu sắc, phông chữ, bố cục
├── js/
│   ├── config.js       ← ⭐ CẤU HÌNH: SĐT, mã PIN, giờ báo cáo
│   ├── tools.js        ← 2 công cụ tính lãi vay & đền bù GPMB
│   ├── gia-an.js       ← Chức năng AI Chat Gia An
│   └── report.js       ← Báo cáo tổng kết cuối ngày
├── images/
│   └── logo.svg        ← Logo thương hiệu (thay file để đổi logo)
├── favicon/
│   └── favicon.svg     ← Biểu tượng trên tab trình duyệt
├── assets/             ← Ảnh, PDF, tài liệu tải về
├── backups/            ← Các bản lưu để khôi phục khi cần
├── netlify.toml        ← Cấu hình Netlify (không cần sửa)
├── vercel.json         ← Cấu hình Vercel (không cần sửa)
├── robots.txt          ← Cho phép Google tìm thấy website
├── .gitignore          ← Danh sách file không đưa lên GitHub
└── README.md           ← File hướng dẫn này
```

---

## 3. ĐƯA MÃ NGUỒN LÊN GITHUB

GitHub là nơi lưu giữ mã nguồn an toàn, vĩnh viễn. Kể cả máy tính hỏng, mã nguồn vẫn còn.

### Bước 1 — Tạo tài khoản

Vào **https://github.com** → **Sign up** → đăng ký bằng email. Miễn phí.

### Bước 2 — Tạo kho lưu trữ (repository)

1. Đăng nhập, bấm dấu **+** góc trên bên phải → **New repository**
2. **Repository name**: `cafe-quy-hoach`
3. Chọn **Private** (riêng tư) hoặc **Public** (công khai) — đều được
4. **KHÔNG** tích "Add a README file" (dự án đã có sẵn)
5. Bấm **Create repository**

### Bước 3 — Tải mã nguồn lên

**Cách dễ nhất — kéo thả, không cần cài phần mềm:**

1. Ở trang repository vừa tạo, bấm **uploading an existing file**
2. Mở thư mục `cafe-quy-hoach` trên máy, **chọn tất cả file và thư mục bên trong** (Ctrl+A / ⌘+A)
3. Kéo thả vào khung trên GitHub
4. Đợi tải xong, ô **Commit changes** ghi: `Phiên bản đầu tiên`
5. Bấm **Commit changes**

> ⚠️ Kéo thả **nội dung bên trong** thư mục, đừng kéo cả thư mục cha vào.

**Cách chuyên nghiệp hơn — dùng dòng lệnh:**

```bash
cd đường/dẫn/tới/cafe-quy-hoach
git init
git add .
git commit -m "Phiên bản đầu tiên"
git branch -M main
git remote add origin https://github.com/TEN-CUA-BAN/cafe-quy-hoach.git
git push -u origin main
```

---

## 4. DEPLOY TỪ GITHUB LÊN NETLIFY

### Bước 1 — Đăng ký Netlify

Vào **https://app.netlify.com** → **Sign up** → chọn **Sign up with GitHub** (đăng nhập bằng chính tài khoản GitHub vừa tạo). Miễn phí.

### Bước 2 — Kết nối kho mã nguồn

1. Bấm **Add new site** → **Import an existing project**
2. Chọn **Deploy with GitHub**
3. Cho phép Netlify truy cập, chọn kho **`cafe-quy-hoach`**

### Bước 3 — Cấu hình

Netlify tự đọc file `netlify.toml` nên các ô đã điền sẵn đúng:

| Mục | Giá trị |
|---|---|
| Build command | *(để trống)* |
| Publish directory | `.` |

Bấm **Deploy site**. Đợi khoảng 30 giây.

### Bước 4 — Đổi tên miền

Website sẽ có địa chỉ ngẫu nhiên kiểu `random-name-123.netlify.app`. Để đổi:

**Site configuration** → **Domain management** → **Options** → **Edit site name** → nhập `cafequyhoach`

Website của bạn: **https://cafequyhoach.netlify.app**

### Bước 5 (tuỳ chọn) — Gắn tên miền riêng

Nếu bạn mua tên miền riêng (ví dụ `cafequyhoach.vn`):
**Domain management** → **Add a domain** → nhập tên miền → làm theo hướng dẫn trỏ DNS.

---

## 5. CẬP NHẬT WEBSITE SAU NÀY

Đây là điểm mạnh nhất: **sửa mã nguồn → đẩy lên GitHub → Netlify tự cập nhật**. Không bao giờ phải tạo website mới.

### Cách sửa nhanh ngay trên GitHub (không cần cài gì)

1. Vào kho `cafe-quy-hoach` trên GitHub
2. Bấm vào file muốn sửa (ví dụ `js/config.js`)
3. Bấm biểu tượng **cây bút ✏️** góc trên bên phải
4. Sửa nội dung
5. Kéo xuống dưới, bấm **Commit changes**

Netlify tự phát hiện thay đổi và cập nhật website trong khoảng **30 giây**. Không cần làm gì thêm.

### Cách sửa trên máy tính rồi đẩy lên

```bash
# Sửa file bằng phần mềm soạn thảo (khuyên dùng VS Code — miễn phí)
git add .
git commit -m "Mô tả ngắn thay đổi vừa làm"
git push
```

---

## 6. NHỮNG CHỖ HAY SỬA NHẤT

| Muốn thay đổi gì | Mở file nào | Tìm dòng nào |
|---|---|---|
| Số điện thoại, Zalo | `js/config.js` | `hotline`, `zaloChinh` |
| Mã PIN bảng điều khiển | `js/config.js` | `matKhauChuQuan` |
| Giờ gửi báo cáo | `js/config.js` | `gioBaoCao` |
| Logo | `images/logo.svg` | thay cả file, giữ nguyên tên |
| Màu sắc toàn trang | `css/style.css` | khối `:root` ở đầu file |
| Nội dung dịch vụ | `index.html` | tìm `<section id="dich-vu"` |
| Lời tư vấn của Gia An | `js/gia-an.js` | đối tượng `CHU_DE` |
| Từ khóa Gia An nhận diện | `js/gia-an.js` | mảng `TU_KHOA` |
| Công thức tính lãi vay | `js/tools.js` | hàm `calcLoan()` |
| Công thức tính đền bù | `js/tools.js` | hàm `calcGPMB()` |

> 💡 **Số điện thoại còn xuất hiện trong `index.html`** ở phần Liên hệ và chân trang. Nếu đổi số, nhớ tìm và sửa cả ở đó (dùng Ctrl+F tìm `0962145185`).

---

## 7. QUY TẮC SAO LƯU (BACKUP)

Thư mục **`backups/`** chứa các bản lưu:

- `v5-goc-2026-07-20.html` — bản gốc một file, đã chạy tốt
- `v6-cau-truc-chuan-2026-07-20/` — bản chuyển sang cấu trúc thư mục chuẩn

### Nguyên tắc trước mỗi lần sửa lớn

Sao chép các file hiện tại vào thư mục mới trong `backups/`, đặt tên theo ngày:

```
backups/v7-them-trang-tin-tuc-2026-08-15/
```

Nếu bản mới có lỗi, chỉ cần chép file cũ từ `backups/` đè trở lại là website về nguyên trạng.

> ✅ **GitHub cũng là một hệ thống backup tự động.** Mỗi lần Commit là một mốc lưu. Vào tab **Commits** trên GitHub có thể xem lại và khôi phục bất kỳ phiên bản nào trong quá khứ.

---

## 8. NÂNG CẤP AI CHAT LÊN AI THẬT (TUỲ CHỌN)

**Hiện tại AI Chat Gia An đã hoạt động tốt** bằng bộ não hội thoại tích hợp sẵn: chạy ngay, không cần internet, không bao giờ báo lỗi, không tốn phí.

Nếu sau này muốn Gia An hiểu được cả những câu hỏi lạ ngoài kịch bản, làm 3 bước sau.

### Bước 1 — Tạo file hàm

Tạo file **`netlify/functions/giaan.js`** với nội dung:

```js
const SYSTEM = `Bạn là GIA AN — trợ lý tư vấn của CAFE QUY HOẠCH
(Minh Bạch – Uy Tín – An Tâm). Lĩnh vực: check quy hoạch, tư vấn luật sư,
công chứng & sang tên sổ đỏ, kết nối mua bán, đền bù GPMB, mua bán đầu tư BĐS,
cấp phép xây dựng, thiết kế & sửa chữa nhà, vay ngân hàng.

TÍNH CÁCH: ấm áp, gần gũi, xưng "mình", gọi khách "anh/chị + tên".
Mỗi lượt chỉ hỏi 1–2 câu.

UY TÍN: bám sát câu hỏi, giải quyết vấn đề cơ bản trước; TUYỆT ĐỐI không bịa
số liệu, hệ số, đơn giá, mức thuế của một thửa đất cụ thể — nói rõ cần hồ sơ gốc nào.

XIN SĐT: chỉ xin SAU KHI đã giúp khách giải quyết vấn đề cơ bản và khách bộc lộ
nhu cầu thật. Xác nhận lại số, hẹn chuyên gia gọi lại trong 2 giờ, miễn phí, bảo mật.

Hệ số K do UBND Thành phố quyết định riêng từng dự án; đơn giá đất = bảng giá UBND × K.
Nhà có phép + hoàn công = bồi thường cao nhất; không phép xây trước thông báo thu hồi
= hỗ trợ một phần; xây sau thông báo thu hồi = không bồi thường.
Hotline/Zalo của quán: 0962 145 185.`;

export default async (req) => {
  const { messages } = await req.json();
  const r = await fetch("https://api.anthropic.com/v1/messages", {
    method: "POST",
    headers: {
      "content-type": "application/json",
      "x-api-key": process.env.ANTHROPIC_API_KEY,
      "anthropic-version": "2023-06-01"
    },
    body: JSON.stringify({
      model: "claude-sonnet-4-6",
      max_tokens: 1000,
      system: SYSTEM,
      messages
    })
  });
  return new Response(await r.text(), {
    headers: { "content-type": "application/json" }
  });
};
```

### Bước 2 — Khai báo khóa API

Netlify → **Site configuration** → **Environment variables** → **Add a variable**:

- Key: `ANTHROPIC_API_KEY`
- Value: khóa lấy tại https://console.anthropic.com

> ⚠️ **Không bao giờ** viết khóa API trực tiếp vào mã nguồn hay đưa lên GitHub.

### Bước 3 — Bật lên

Mở `js/config.js`, sửa dòng cuối:

```js
apiUrl: '/.netlify/functions/giaan'
```

Xong. Nếu AI gặp sự cố, website **tự động quay về bộ não tích hợp** — khách không bao giờ thấy lỗi.

---

## 9. DEPLOY LÊN VERCEL (TUỲ CHỌN)

Nếu muốn dùng Vercel thay Netlify:

1. Vào https://vercel.com → đăng nhập bằng GitHub
2. **Add New** → **Project** → chọn kho `cafe-quy-hoach`
3. Framework Preset: **Other** — để trống mọi ô build
4. **Deploy**

File `vercel.json` đã cấu hình sẵn.

---

## 10. XỬ LÝ SỰ CỐ THƯỜNG GẶP

| Hiện tượng | Nguyên nhân & cách xử lý |
|---|---|
| Trang trắng, mất hết màu | Sai đường dẫn thư mục. Kiểm tra `css/` và `js/` nằm cùng cấp với `index.html` |
| Logo không hiện | Thiếu file `images/logo.svg`, hoặc tên file viết hoa/thường sai |
| Nút bấm không phản ứng | Nhấn **F12** → tab **Console** xem báo lỗi ở file nào, dòng nào |
| Sửa xong web không đổi | Nhấn **Ctrl+F5** (hoặc ⌘+Shift+R) để tải lại bỏ qua bộ nhớ đệm |
| Netlify không cập nhật | Vào tab **Deploys** xem trạng thái; bấm **Trigger deploy** để chạy lại |
| Báo cáo cuối ngày trống | Chưa có khách chat trong ngày, hoặc mở bằng trình duyệt khác (dữ liệu lưu theo từng trình duyệt) |
| Quên mã PIN | Mở `js/config.js`, xem dòng `matKhauChuQuan` |

---

## THÔNG TIN LIÊN HỆ

- **Hotline / Zalo chính:** 0962 145 185
- **Hotline 2:** 0988 252 979

---

## GHI CHÚ VỀ QUYỀN SỞ HỮU

Toàn bộ mã nguồn trong dự án này thuộc về **Cafe Quy Hoạch**. Website chạy hoàn toàn bằng HTML, CSS và JavaScript tiêu chuẩn — không lệ thuộc vào bất kỳ nền tảng, công cụ hay dịch vụ AI nào. Miễn là bạn còn giữ thư mục mã nguồn này (trên máy tính hoặc trên GitHub), website sẽ không bao giờ bị mất và luôn có thể triển khai lại ở bất cứ đâu.

---

*Cập nhật lần cuối: 20/07/2026 — phiên bản cấu trúc chuẩn*
