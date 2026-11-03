# Lab 1 — Nhập môn kiểm thử tự động & Thiết lập môi trường

Selenium WebDriver + C# + NUnit (.NET).

## Cấu trúc

```
SeleniumLab1/
├── FirstTests/
│   ├── FirstTests.csproj
│   └── FirstSeleniumTest.cs   # kịch bản Selenium đầu tiên
├── screenshots/               # ảnh minh chứng
├── .gitignore                 # tạo bằng `dotnet new gitignore`
└── README.md
```

## Yêu cầu môi trường

- .NET SDK (kiểm tra: `dotnet --version`)
- Google Chrome (bản mới)
- Visual Studio hoặc VS Code + C# Dev Kit
- Không cần tải ChromeDriver thủ công: Selenium 4.6+ có Selenium Manager tự tải driver phù hợp với Chrome.

## Cách chạy

```bash
cd FirstTests
dotnet restore
dotnet test --logger "console;verbosity=detailed"
```

Chrome sẽ tự mở tới https://example.com, in tiêu đề trang, kiểm tra bằng Assert rồi đóng bằng `Quit()`.

## Kịch bản test

| Bước | Hành động |
|------|-----------|
| 1 | Khởi tạo `ChromeDriver` |
| 2 | `Navigate().GoToUrl("https://example.com")` |
| 3 | Đọc `driver.Title` và in ra |
| 4 | `Assert.That(title, Is.EqualTo("Example Domain"))` |
| 5 | `driver.Quit()` (trong `finally`) |

## Minh chứng (thư mục `screenshots/`)

- `01-dotnet-version.png` — kết quả `dotnet --version`
- `02-dotnet-info.png` — kết quả `dotnet --info`
- `03-csproj.png` — file `.csproj` có `Selenium.WebDriver`
- `04-test-passed.png` — kết quả test **Passed**
- `05-first-commit.png` — `git init` và commit lần 1
- `05-git-log.png` — lịch sử commit (`git log --oneline`)
- `06-ai-prompt.png` — ảnh prompt và câu trả lời của AI (Phần D)
- `07-github-repo.png` — trang repository trên GitHub

## Phần D — Trải nghiệm dùng AI

**Tình huống:** Khi đổi tên ảnh minh chứng bằng PowerShell, tôi chạy lại lệnh `Rename-Item` thì báo lỗi: `Rename-Item : Cannot rename because item at '01-dotnet-version.png.png' does not exist.`

**Prompt đã dùng:** Tôi sao chép nguyên văn thông báo lỗi trên vào ô tìm kiếm Google và dùng phần "Tổng quan về AI" để hỏi lỗi này nghĩa là gì và có cần sửa gì không. (Ảnh chụp: `screenshots/06-ai-prompt.png`)

**Câu trả lời nhận được (tóm tắt):** AI giải thích PowerShell không tìm thấy tệp có tên `01-dotnet-version.png.png` trong thư mục hiện tại, và đuôi `.png.png` thường xuất hiện vì Windows ẩn đuôi tệp nên người dùng vô tình gõ thêm `.png`.

**Kết quả:** Tôi chạy `dir` và `git status` để kiểm tra. Các ảnh đã có đúng tên một đuôi `.png`, vì lần chạy đầu đã đổi tên thành công, lỗi chỉ xuất hiện khi tôi chạy lại lệnh lần hai. Tôi không cần sửa gì thêm.

**Nhận xét:** AI hữu ích vì giải thích đúng ý nghĩa thông báo lỗi và nguyên nhân phổ biến của đuôi `.png.png` là Windows ẩn đuôi tệp. Tuy nhiên AI chưa chính xác vì chỉ đoán chung chung, không biết lệnh đã chạy thành công ở lần đầu, và câu "phải sửa nếu" làm người đọc tưởng có gì đó đang hỏng. Vì vậy tôi tự kiểm tra bằng `dir` và `git status` trước khi quyết định, đúng như hướng dẫn "luôn tự kiểm chứng gợi ý của AI".