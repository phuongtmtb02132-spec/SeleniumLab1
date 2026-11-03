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
- `05-git-log.png` — lịch sử commit (`git log --oneline`)
- `06-ai-prompt.png` — ảnh prompt/câu trả lời AI (Phần D)

## Phần D — Trải nghiệm dùng AI
> ⚠️ Hãy sửa lại mục này theo đúng tình huống THỰC TẾ bạn gặp khi làm bài.

**Tình huống:** (ví dụ) Sau khi cài .NET SDK, gõ `dotnet --version` thì báo `command not found` / `'dotnet' is not recognized`.

**Prompt đã dùng:**
> Tôi đang dùng Windows 11, vừa cài .NET SDK để viết test Selenium bằng C#. Khi chạy `dotnet --version` trong terminal thì báo lỗi: `'dotnet' is not recognized as an internal or external command`. Nguyên nhân có thể là gì và cách khắc phục?

**Câu trả lời nhận được (tóm tắt):** AI giải thích terminal chưa nạp lại biến môi trường PATH sau khi cài; gợi ý đóng hẳn và mở lại terminal, kiểm tra thư mục `C:\Program Files\dotnet` có trong PATH.

**Kết quả:** Đóng và mở lại terminal, `dotnet --version` hiển thị phiên bản đúng.

**Nhận xét:**
AI giúp xác định nhanh nguyên nhân và đưa ra các bước khắc phục cụ thể, tiết kiệm thời gian tìm kiếm. Tuy nhiên AI đôi khi gợi ý phiên bản gói hoặc cú pháp cũ (ví dụ cách khởi tạo ChromeDriver kèm đường dẫn driver thủ công, nay không còn cần thiết vì đã có Selenium Manager), nên tôi luôn đối chiếu với tài liệu chính thức và tự chạy thử trước khi áp dụng. AI hỗ trợ tốt nhưng không thay thế việc hiểu rõ lỗi và tự kiểm chứng.
