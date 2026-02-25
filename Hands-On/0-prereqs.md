# 演習 0: 環境の準備と設定

| | [次の手順: ウェブサイトの探索と機能理解 →][next-lesson] |
|:--|--:|

この演習を開始する前に、必要なソフトウェアやツールが準備されていることを確認しましょう。

## シナリオ

ウェブサイトのテスト作成に取り掛かる前に、作業に必要なソフトウェアやツールを準備します。適切な環境設定により、スムーズにテスト作成作業を進めることができます。

## 必須 1. 作業環境の確認

以下のソフトウェアとツールが使えることを確認してください：

1. **Windows PowerShell**: コマンド実行用（管理者権限で実行可能）
2. **Git**: バージョン管理システム（インストール済み）
3. **Node.js**: JavaScript実行環境（バージョン 16 以上）
4. **Visual Studio Code**: コードエディター（GitHub Copilot拡張機能有効）
5. **ブラウザ**: Chrome、Edge、Firefoxのいずれか

**バージョン確認コマンド**:
```powershell
node --version
npm --version
```

<details>
<summary><strong>Node.jsが未インストールの場合</strong></summary>

1. [Node.js公式サイト](https://nodejs.org/) からLTS版をダウンロード
2. ダウンロードした`.msi`ファイルを実行してインストール
3. PowerShellを再起動してバージョン確認

</details>


## 必須 2. プロジェクトのセットアップ

演習用ファイルをダウンロードし、作業環境を準備します。

**PowerShellを管理者権限で起動し、以下のコマンドを順番に実行してください**:

```powershell
# 作業用フォルダを作成・移動（お好きな場所を指定してください）
# 例: C:\work、C:\Users\YourName\Desktop、D:\projects など
New-Item -ItemType Directory -Force -Path C:\work
cd C:\work

# プロジェクトをクローン（講師から提供されたURLを使用してください）
git clone <講師提供のリポジトリURL>
cd ACM-Hands-On-Demo-1-1

# 作業用ブランチを作成
git checkout JP-translation
git pull origin JP-translation
git checkout -b feature/e2e-test-creation

# Node.jsプロジェクトを初期化
npm init -y

# Playwrightをインストール
npm install --save-dev @playwright/test
```

**VS Codeでプロジェクトを開く**:
- VS Codeの「ファイル」→「フォルダーを開く」
- `C:\work\ACM-Hands-On-Demo-1-1` を選択

## 必須 3. 動作確認

以下を確認して、セットアップが正しく完了したことを確認してください：

**確認項目**:
- [ ] VS Codeで `ACM-Hands-On-Demo-1-1` フォルダーが開いている
- [ ] `package.json` ファイルが作成されている
- [ ] GitHub Copilot拡張機能が有効（VS Code右下にCopilotアイコン表示）
- [ ] ブランチが `feature/e2e-test-creation` になっている

## トラブルシューティング

**よくあるエラーと解決方法**:

| エラー | 解決方法 |
|--------|----------|
| `git` コマンドが認識されない | Gitをインストールし、PowerShellを再起動 |
| `node` コマンドが認識されない | Node.jsをインストールし、PCを再起動 |
| Copilotが動作しない | VS CodeでGitHubアカウントに再ログイン |
| PowerShell実行ポリシーエラー | `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` を実行 |

**詳細なサポート**:
- 問題が解決しない場合は、講師またはサポートスタッフにお声がけください

## まとめと次のステップ

環境準備が完了しました。次のステップでは、Smart Bookmarksウェブサイトを詳しく探索して、AIアシスタントでテストする機能を特定します。

実際にウェブサイトを操作することで、利用者の視点からサイトの動きを理解し、AIプロンプト作成の基礎を作ります。

## リソース

- [GitHub Copilot公式ドキュメント](https://docs.github.com/copilot)
- [Visual Studio Code拡張機能管理](https://code.visualstudio.com/docs/editor/extension-marketplace)
- [PowerShell実行ポリシー](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)

---

| | [次の手順: ウェブサイトの探索と機能理解 →][next-lesson] |
|:--|--:|

[next-lesson]: ./1-explore-website.md