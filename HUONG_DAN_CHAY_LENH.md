# Các lệnh cần chạy theo thứ tự (làm trên máy của bạn)

## Phần A
```bash
# Windows: choco install dotnet-sdk -y   |  macOS: brew install --cask dotnet-sdk
# (hoặc tải bản cài từ https://dotnet.microsoft.com/download)
dotnet --version     # chụp ảnh -> screenshots/01-dotnet-version.png
dotnet --info        # chụp ảnh -> screenshots/02-dotnet-info.png

dotnet new nunit -n FirstTests
cd FirstTests
dotnet add package Selenium.WebDriver
# Mở FirstTests.csproj, chụp ảnh -> screenshots/03-csproj.png
```

## Phần B
```bash
# Xoá UnitTest1.cs, chép FirstSeleniumTest.cs vào thư mục FirstTests/
dotnet test --logger "console;verbosity=detailed"
# Chụp ảnh kết quả Passed -> screenshots/04-test-passed.png
```

## Phần C
```bash
cd ..                      # về thư mục gốc SeleniumLab1
dotnet new gitignore       # tạo .gitignore (đã loại bin/ obj/)
git init
git add .gitignore README.md
git commit -m "chore: add .gitignore and README for Lab 1"
git add .
git commit -m "feat: add NUnit project with first Selenium test (check page title)"
git log --oneline          # chụp ảnh -> screenshots/05-git-log.png
git add screenshots
git commit -m "docs: add evidence screenshots"

# Tạo repo PUBLIC trên github.com (không tick README/.gitignore), rồi:
git branch -M main
git remote add origin https://github.com/<ten-ban>/<ten-repo>.git
git push -u origin main
```
