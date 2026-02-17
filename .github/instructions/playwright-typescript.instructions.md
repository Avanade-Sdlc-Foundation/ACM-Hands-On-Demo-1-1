---
description: 'Playwright テスト生成指示'
applyTo: '**'
---

## テスト作成ガイドライン

### コード品質基準
- **ロケーター**: 耐久性とアクセシビリティのため、ユーザー向けで role ベースのロケーター（`getByRole`、`getByLabel`、`getByText` など）を優先してください。`test.step()` を使って操作をグルーピングし、テストの可読性とレポート性を向上させてください。
- **アサーション**: 自動リトライされる web-first アサーションを使用してください。これらのアサーションは `await` で始まります（例: `await expect(locator).toHaveText()`）。可視性の変化を特にテストする場合を除き、`expect(locator).toBeVisible()` は避けてください。
- **タイムアウト**: Playwright の組み込み auto-wait を活用してください。ハードコードした wait や、デフォルトタイムアウトの増加は避けてください。
- **明確さ**: 意図が明確に伝わる、説明的なテスト名・ステップ名を使用してください。コメントは、複雑なロジックや直感的でない操作を説明する必要がある場合にのみ追加してください。


### テスト構成
- **Imports**: `import { test, expect } from '@playwright/test';` から始めてください。
- **Organization**: 機能に関連するテストは `test.describe()` ブロック配下にまとめてください。
- **Hooks**: `describe` ブロック内のすべてのテストで共通のセットアップ（例: ページ遷移）は `beforeEach` を使用してください。
- **Titles**: `Feature - Specific action or scenario` のような明確な命名規則に従ってください。


### ファイル構成
- **Location**: すべてのテストファイルは `tests/` ディレクトリに格納してください。
- **Naming**: `<feature-or-page>.spec.ts` の規則に従ってください（例: `login.spec.ts`、`search.spec.ts`）。
- **Scope**: 主要なアプリ機能またはページごとに、テストファイルは 1 つを目安にしてください。

### アサーションのベストプラクティス
- **UI 構造**: コンポーネントのアクセシビリティツリー構造を検証するには `toMatchAriaSnapshot` を使用してください。これは包括的でアクセシブルなスナップショットを提供します。
- **要素数**: ロケーターで見つかった要素数の検証には `toHaveCount` を使用してください。
- **テキスト内容**: 完全一致は `toHaveText`、部分一致は `toContainText` を使用してください。
- **ナビゲーション**: 操作後のページ URL を検証するには `toHaveURL` を使用してください。


## テスト構成例

```typescript
import { test, expect } from '@playwright/test';

test.describe('映画検索機能', () => {
  test.beforeEach(async ({ page }) => {
    // 各テスト前にアプリケーションに遷移
    await page.goto('https://debs-obrien.github.io/playwright-movies-app');
  });

  test('タイトルで映画を検索', async ({ page }) => {
    await test.step('検索の実行', async () => {
      await page.getByRole('search').click();
      const searchInput = page.getByRole('textbox', { name: '検索入力' });
      await searchInput.fill('Garfield');
      await searchInput.press('Enter');
    });

    await test.step('検索結果の検証', async () => {
      // 検索結果のアクセシビリティツリーを検証
      await expect(page.getByRole('main')).toMatchAriaSnapshot(`
        - main:
          - heading "Garfield" [level=1]
          - heading "検索結果" [level=2]
          - list "映画一覧":
            - listitem "映画":
              - link "ザ・ガーフィールド・ムービーのポスター ザ・ガーフィールド・ムービー 評価":
                - /url: /playwright-movies-app/movie?id=tt5779228&page=1
                - img "ザ・ガーフィールド・ムービーのポスター"
                - heading "ザ・ガーフィールド・ムービー" [level=2]
      `);
    });
  });
});
```

## テスト実行戦略

1. **初回実行**: `npx playwright test --project=chromium` でテストを実行
2. **失敗のデバッグ**: テスト失敗を分析し、根本原因を特定
3. **反復**: ロケーター、アサーション、テストロジックを必要に応じて改善
4. **検証**: テストが安定して合格し、意図した機能をカバーしていることを確認
5. **報告**: 実行結果と発見した問題点をフィードバック

## 品質チェックリスト

最終化前に以下を確認:
- [ ] すべてのロケーターがアクセシブルで十分に具体的であり、strict mode 違反を避けている
- [ ] テストが論理的にグルーピングされ、明確な構成に従っている
- [ ] アサーションが意味のあるもので、ユーザー期待に沿っている
- [ ] テスト命名規則が一貫している
- [ ] コードが適切に整形され、必要な場合のみコメントが付与されている