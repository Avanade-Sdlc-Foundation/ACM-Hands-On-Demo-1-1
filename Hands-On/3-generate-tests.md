# 演習 3: GitHub Copilot Chatによるテストコード生成

| [← 前の手順][previous-lesson] | |
|:--|--:|

GitHub Copilot Chatを活用して、Smart Bookmarksの機能に対応したPlaywright E2Eテストコードを生成します。

## シナリオ

品質保証チームでは、手動テスト作成の時間短縮と品質向上を目的として、AI支援によるテストコード生成を導入します。あなたは、GitHub Copilot Chatを使用してカテゴリフィルタリング機能のE2Eテストを実装し、プロジェクトのコーディング規約に準拠したテストスイートを構築します。

適切なプロンプト設計により、保守しやすく理解しやすいテストコードを生成し、継続的インテグレーションに組み込める品質を確保します。

## ? 必須 1. GitHub Copilot Chatの起動

VS Code環境でGitHub Copilot Chatを有効化し、テストコード生成に備えます。

1. **Copilot Chatビューの開き方**:
   - VS Codeの右サイドバーにあるチャットアイコン（?）をクリック
   - Copilot Chatビューが右側に表示されることを確認
![alt text](./images/caht-icon.png)


## ? 必須 2. プロンプト設計による効果的なテストコード生成

プロジェクトの品質基準に従った詳細なプロンプトを作成します。

1. **基本プロンプトの入力**:
   Copilot Chatに以下のプロンプトを入力してください：

   ```
   https://ravi-cheetiralaav.github.io/smart-bookmarks のカテゴリによる表示内容切り替え機能について、Playwright（TypeScript）の E2E テストコードを生成してください。

   - テストは `tests/category-filter.spec.ts` に作成する想定でお願いします。
   - ロケーターはユーザー向けの role ベース（`getByRole` / `getByLabel` / `getByText` など）を優先してください。
   - 操作は `test.step()` で目的ごとにグルーピングしてください。
   - アサーションは auto-retrying な web-first assertion（例: `await expect(locator).toHaveText()`）を使ってください。
   - ハードコード待機（`waitForTimeout` など）は避けてください。
   ```

2. **プロンプト送信と初回回答の受信**:
   - Enterキーまたは送信ボタンでプロンプトを送信
   - Copilot Chatが回答を生成するまで待機
   - 生成されたテストコードの全体構造を確認

## ? 必須 3. 生成されたテストコードの詳細分析

Copilot Chatが生成したコードの品質と適合性を評価します。

1. **コード構造の確認**:
   - 適切なimport文が含まれているか
   - `test.describe`ブロックによるテストグルーピング
   - `test.beforeEach`での共通セットアップ
   - 明確なテスト名の付与

2. **期待されるコード構造例**:
   ```typescript
   import { test, expect } from '@playwright/test';

   test.describe('Category Filter - Switch displayed bookmarks by category', () => {
     test.beforeEach(async ({ page }) => {
       await page.goto('https://ravi-cheetiralaav.github.io/smart-bookmarks');
     });

     test('Category Filter - switching category updates the bookmark list', async ({ page }) => {
       await test.step('Confirm initial category and list', async () => {
         // 初期状態の確認
       });

       await test.step('Switch category and verify filtered result', async () => {
         // カテゴリ切り替えと結果確認
       });
     });
   });
   ```

3. **プロジェクト規約への適合性確認**:
   - ロケーター戦略がroleベースになっているか
   - `test.step()`による適切なグルーピング
   - web-first assertionの使用
   - ハードコード待機の回避


## ? 参考 4. テストコードのレビューと理解

生成されたコードの各部分の動作と意図を理解します。

1. **ロケーター戦略の理解**:
   - `getByRole('button')` - ボタン要素の特定
   - `getByText('AI')` - テキストによる要素特定
   - `getByLabel()` - ラベルによるフォームコントロール特定

2. **アサーション戦略の理解**:
   - `toHaveText()` - テキスト内容の完全一致
   - `toContainText()` - テキスト内容の部分一致
   - `toBeVisible()` - 要素の可視性確認
   - `toHaveCount()` - 要素数の確認

3. **test.step()の効果的な使用**:
   - テスト手順の論理的な分割
   - レポートでの可読性向上
   - デバッグ時の問題箇所特定の簡易化



## ?? トラブルシューティング

### Copilot Chatが応答しない場合

1. **接続状況の確認**:
   - インターネット接続が安定しているか確認
   - VS Codeの下部ステータスバーでCopilot の状態確認

2. **再認証の実行**:
   - VS Codeコマンドパレット（Ctrl+Shift+P）を開く
   - 「GitHub Copilot: Sign Out」を実行
   - 再度サインインを実行

### 生成されたコードに問題がある場合

1. **プロンプトの修正**:
   - より具体的で詳細なプロンプトに修正
   - プロジェクト固有の要件を明確に指定

2. **段階的な生成**:
   - 一度に全てを生成せず、段階的に機能を追加
   - 各ステップでの確認とフィードバック

### TypeScript/Playwright関連のエラー

1. **依存関係の確認**:
   ```powershell
   # package.jsonの確認
   Get-Content package.json
   # 必要に応じてPlaywrightのインストール
   npm install @playwright/test
   ```

2. **設定ファイルの確認**:
   - playwright.config.ts の設定を確認
   - tsconfig.json のTypeScript設定を確認

## まとめと次のステップ

GitHub Copilot Chatを活用したE2Eテストコード生成が完了しました：

- **効率的なプロンプト設計**: プロジェクト要件を明確に伝える技術
- **品質の高いテストコード**: プロジェクト規約に準拠した実装
- **AI支援開発プロセス**: 手動作業の大幅な削減と品質向上

### 習得したスキル

- **GitHub Copilot Chatの効果的な活用**: 適切なプロンプトによるコード生成
- **Playwrightテスト理解**: ブラウザ自動化テストの基本パターン
- **Custom指示の活用**: プロジェクト固有のルールに従った開発
- **テストコードレビュー**: 生成されたコードの品質評価能力

### 今後の展開

生成されたテストコードをベースに、以下の拡張を検討してください：

- 他の機能（タグフィルタリング、検索機能等）のテストケース追加
- パフォーマンステストやアクセシビリティテストの実装
- 継続的インテグレーション（CI/CD）パイプラインへの組み込み

## リソース

- [GitHub Copilot 公式ドキュメント](https://docs.github.com/copilot)
- [Playwright 公式ドキュメント](https://playwright.dev/)
- [TypeScript 公式ドキュメント](https://www.typescriptlang.org/docs/)

---

| [← 前の手順][previous-lesson] | |
|:--|--:|

[previous-lesson]: ./2-setup-environment.md