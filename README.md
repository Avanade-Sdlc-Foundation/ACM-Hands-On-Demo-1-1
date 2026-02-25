# ACM Hands-On Demo: ウェブサイト動作テストの自動生成

AIアシスタント（GitHub Copilot Chat）を使って、ウェブサイトの動作テストを簡単に作る体験型の演習です。

## 概要

この演習では、AIアシスタントを使ってウェブサイトの動作テストを自動で作る新しい方法を学びます。「Smart Bookmarks」という書籍管理ウェブサイトを使って、これまでの手作業でのテスト作成から、AIを活用した効率的なテスト作成への新しいやり方を体験できます。

## シナリオ

あなたは書籍管理ウェブサイト「Smart Bookmarks」の品質管理チームのメンバーです。新しい機能をリリースする前に、ウェブサイトが正常に動作するかを確認するテストが必要になりました。

従来のように手作業でテストを作るのは時間がかかるため、AIアシスタントを活用して効率的にテストプログラムを作成し、自動でテストが実行できるようにします。

## ? ハンズオン演習

実際の演習は以下のリンクから開始できます：

**[? Hands-On: ウェブサイト動作テストの作成](./Hands-On/README.md)**

## プロジェクト構成

```
├── Demo Scenario.md          # 演習シナリオの詳細
├── exercise.md               # 基本的な演習手順
├── Hands-On/                 # メインのハンズオン教材
│   ├── README.md            # 演習の概要と目次
│   ├── 0-prereqs.md         # 前提条件
│   ├── 1-explore-website.md # ウェブサイト探索
│   ├── 2-setup-environment.md # 環境セットアップ
│   ├── 3-generate-tests.md  # テスト生成
│   └── images/              # スクリーンショット等
└── tests/                   # 生成されるテストファイル
```

## 使用するツールとサイト

- **練習用ウェブサイト**: [Smart Bookmarks](https://ravi-cheetiralaav.github.io/smart-bookmarks)（書籍管理サイト）
- **テスト作成ツール**: Playwright（ブラウザ自動化ツール）
- **AIアシスタント**: GitHub Copilot Chat

## 必要な環境

- **Visual Studio Code**: コードを書くためのエディター
- **Node.js**: JavaScript を実行するための環境（バージョン 18 以上）
- **GitHub Copilot Chat 拡張機能**: AI アシスタント機能
- **基本的なプログラミング知識**: JavaScript/TypeScript の基礎があると理解しやすいです

## 始め方

1. このプロジェクトフォルダをダウンロード
2. [Hands-On演習](./Hands-On/README.md) のページを開く
3. [環境の準備](./Hands-On/0-prereqs.md) から順番に開始

---

## ? 追加リソース

- [Playwright 公式ドキュメント](https://playwright.dev/)
- [GitHub Copilot Chat Documentation](https://docs.github.com/en/copilot/github-copilot-chat)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)

> [!NOTE]  
> この演習で使用するAIツールは学習に基づいて動作するため、画面の表示や
> 生成されるコードが説明と多少異なる場合があります。

**? [今すぐハンズオンを開始する →](./Hands-On/README.md)**