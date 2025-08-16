# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

autosave.nvim - Neovimに自動保存機能を提供するシンプルなプラグイン。vim-auto-saveにインスパイアされて作成された。

## コードアーキテクチャ

- **メインモジュール**: `lua/autosave.lua` - すべての機能が単一ファイルに実装
- **設定管理**: `setup()` 関数で設定を受け取り、デフォルト設定とマージ
- **イベント駆動**: Neovimのautocmdを使用して指定イベント時に自動保存を実行
- **コマンド**: `:AutosaveEnable`, `:AutosaveDisable`, `:AutosaveToggle` を提供

## 開発コマンド

### コードフォーマット
```bash
stylua lua/
```

### 動作確認
Neovimで直接プラグインをロードして動作確認:
```lua
require('autosave').setup()
```

## 重要な実装詳細

- 無名バッファはスキップされる
- 変更されていないファイルは保存されない
- `vim.cmd("silent! update")` で実際の保存を実行
- `exclude_filetypes` 設定により特定のファイルタイプで自動保存を無効化可能（oil.nvim等との互換性のため）
