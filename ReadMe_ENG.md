# ToolChain README

本ディレクトリは、SolidDesigner のビルドおよびコード生成に必要なツール一式をプロジェクト内に同梱するためのものです。
開発環境に依存せず、CI/新規PCでも同一手順でビルドできることを目的とします。

## 構成
- `Python310/` : 生成スクリプト実行用の Python 3.10（同梱版）
  - 例：`Python310/python.exe`

## 使い方（CMake）
CMake では同梱 Python を優先して使用してください。

例：
- `Python3_EXECUTABLE` を `.../ToolChain/Python310/python.exe` に固定
- `find_package(Python3 COMPONENTS Interpreter REQUIRED)` の前に設定する

（これにより `CommandsConfig.xml` → `SolidDesignerCommands.h` 等の生成処理が安定します。）

## 注意事項
- `generated/` などの生成物はビルドディレクトリ側に出力し、リポジトリには含めない運用を推奨します。
- Windows の embeddable Python を同梱している場合、`python310._pth` や標準ライブラリパス設定によりスクリプトが動作しないことがあります。
  その際は ToolChain 側の Python 構成を見直してください。

