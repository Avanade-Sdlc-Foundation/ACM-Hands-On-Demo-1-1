# 演習 0: 前提条件と環境設定

| | [次の手順: ウェブサイトの探索と機能理解 →][next-lesson] |
|:--|--:|

この演習を開始する前に、必要な環境とツールが準備されていることを確認しましょう。

## シナリオ

E2Eテストの実装に取り掛かる前に、開発チームの標準環境を構築します。適切な環境設定により、チーム全体で一貫したテスト開発プロセスを実現できます。

## ? 必須 1. 開発環境の確認

以下の環境とツールが利用可能であることを確認してください：

1. **Windows PowerShell**: 管理者権限で実行可能であること
2. **Git**: バージョン管理システムがインストールされていること
3. **Visual Studio Code**: 最新版がインストールされていること
4. **GitHub Copilot**: VS Code拡張機能が有効化されていること
5. **ブラウザ**: Chrome、Edge、Firefoxのいずれかが利用可能であること

## ? 必須 2. GitHub Copilotの準備

GitHub Copilotが正常に動作することを確認してください：

1. **ライセンス確認**: GitHub Copilotのサブスクリプションが有効であること
2. **VS Code拡張機能**: 「GitHub Copilot」および「GitHub Copilot Chat」がインストール・有効化されていること
3. **認証状態**: GitHubアカウントにサインインしていること

## ? 必須 3. ネットワークアクセスの確認

以下のリソースにアクセス可能であることを確認してください：

1. **テスト対象サイト**: https://ravi-cheetiralaav.github.io/smart-bookmarks
2. **GitHub リポジトリ**: https://github.com/Avanade-Sdlc-Foundation/ACM-Hands-On-Demo-1-1.git
3. **インターネット接続**: 画像やリソースの読み込みが正常に行われること

## ? 参考 4. 基礎知識の確認

以下の知識があると演習がスムーズに進行します：

1. **Git基本操作**: clone、branch、checkout、pullコマンドの理解
2. **PowerShell基本操作**: コマンド実行、ディレクトリ操作の基礎知識
3. **VS Code基本操作**: ファイル操作、拡張機能の使用方法
4. **Web技術基礎**: HTML、CSS、JavaScriptの基本概念


## ?? トラブルシューティング

### GitHub Copilotが動作しない場合

1. **ライセンスの確認**: GitHub設定でCopilotサブスクリプションの状態を確認
2. **再認証**: VS CodeでGitHubアカウントからサインアウト後、再度サインイン
3. **拡張機能の再有効化**: GitHub Copilot拡張機能を無効化後、再度有効化

### ネットワークアクセスの問題

1. **プロキシ設定**: 企業環境ではIT部門にプロキシ設定を確認
2. **ファイアウォール**: セキュリティソフトがアクセスをブロックしていないか確認
3. **代替ネットワーク**: 可能であれば別のネットワーク環境で試行

### PowerShell実行ポリシーエラー

1. **実行ポリシーの確認**: `Get-ExecutionPolicy` で現在の設定を確認
2. **一時的な変更**: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
3. **管理者権限**: PowerShellを管理者として実行

## まとめと次のステップ

環境準備が完了しました。次のステップでは、テスト対象となるSmart Bookmarksウェブサイトを詳しく探索し、テストすべき機能を特定します。

実際のウェブサイトを操作することで、ユーザーの視点からアプリケーションの動作を理解し、効果的なテストケースを設計する基盤を築きます。

## リソース

- [GitHub Copilot公式ドキュメント](https://docs.github.com/copilot)
- [Visual Studio Code拡張機能管理](https://code.visualstudio.com/docs/editor/extension-marketplace)
- [PowerShell実行ポリシー](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)

---

| | [次の手順: ウェブサイトの探索と機能理解 →][next-lesson] |
|:--|--:|

[next-lesson]: ./1-explore-website.md