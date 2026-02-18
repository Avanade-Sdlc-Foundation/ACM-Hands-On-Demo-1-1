# 演習: Smart Bookmarks ウェブサイトの探索

## 目的
ウェブサイト [Smart Bookmarks](https://ravi-cheetiralaav.github.io/smart-bookmarks) を探索し、その機能とユーザーインターフェイスに慣れ、ブラウザ E2E テストケースを生成してください。

## 手順
1. **ウェブサイトの探索**: 上記の URL にアクセスし、Smart Bookmarks ウェブサイトを探索してください。利用可能な機能、ユーザーインターフェイスの要素、およびユーザーがどのように操作するかを理解してください。
2. **機能の特定**: ウェブサイトの主要な機能を特定してください。例えば、ブックマークの追加、編集、削除、検索機能などがあります。
3. **テストケースの生成**: 各機能に対して、CopilotChat に以下のプロンプトを書いてあげます。

>プロンプト例:
```
https://ravi-cheetiralaav.github.io/smart-bookmarks のカテゴリによる表示内容切り替え機能について、Playwright（TypeScript）の E2E テストコードを生成してください。
- テストは `tests/category-filter.spec.ts` に作成する想定でお願いします。
- ロケーターはユーザー向けの role ベース（`getByRole` / `getByLabel` / `getByText` など）を優先してください。
- 操作は `test.step()` で目的ごとにグルーピングしてください。
- アサーションは auto-retrying な web-first assertion（例: `await expect(locator).toHaveText()`）を使ってください。
- ハードコード待機（`waitForTimeout` など）は避けてください。
```

4. **回答の確認**: CopilotChat が生成したテストコードを確認し、必要に応じて修正や追加を行ってください。

>回答例（イメージ）:
```typescript
import { test, expect } from '@playwright/test';

test.describe('Category Filter - Switch displayed bookmarks by category', () => {
  test.beforeEach(async ({ page }) => {
    await page.goto('https://ravi-cheetiralaav.github.io/smart-bookmarks');
  });

  test('Category Filter - switching category updates the bookmark list', async ({ page }) => {
    await test.step('Confirm initial category and list', async () => {
      // ...
    });

    await test.step('Switch category and verify filtered result', async () => {
      // ...
    });
  });
});
