本项目GitHub action workflow 构建脚本：

  1. checkout 当前 patch 项目，读取 TestKey.jks
  2. clone https://github.com/gedoor/legado.git
  3. 写入固定签名配置
  4. 从 app/build.gradle 删除 Firebase bom、analytics、perf 三个依赖
  5. 注释 alias libs.plugins.google.services
  6. 删除上游源码里的 app/google-services.json
  7. 注入 ndk { abiFilters "arm64-v8a" }
  8. 执行 ./gradlew assembleAppRelease
  9. 上传 APK 和 mapping artifact