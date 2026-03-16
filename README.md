配置 .net framework 4.5 开发环境的 GitHub action。只能用于 windows 容器。  
GitHub action for configuring .net framework 4.5 SDK. For windows runner only!

### 用法 Usage

```yaml
name: .net framework CI

on: [push]

jobs:
  build:
    runs-on: windows-2025

    steps:
      - uses: actions/checkout@v6

      - name: Setup net45 SDK
        uses: vrnobody/setup-net45@v1.24.0

      - name: Restore Nuget packages
        run: nuget restore MyProject.sln

      - name: Build solution
        run: msbuild MyProject.sln -p:Configuration=Release

      - name: Run unit tests
        run: |
          function Invoke-VSTest {
            & "vstest.console.exe" $args
            if(-not $?){ throw "fail!" }
          }
          Invoke-VSTest "MyTestProject/bin/Release/MyTestProject.Test.dll"
```

### 开发 Development

```bash
git clone https://github.com/vrnobody/setup-net45.git
cd setup-net45
npm install
npm run build
```

### 更新日志

[update-log.md](./docs/update-log.md)

### 感谢 Credits

https://github.com/warrenbuckley/Setup-Nuget  
https://github.com/warrenbuckley/Setup-MSBuild  
https://github.com/Malcolmnixon/Setup-VSTest
