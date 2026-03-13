# 百花ジェル 通販サイト

医療法人百花繚乱が監修する「百花ジェル」の通販サイトです。

## 特徴

- Waphytoを参考にした上品なデザイン
- 余白を活かした視認性の高いレイアウト
- モバイルファーストのレスポンシブデザイン
- コンポーネント化された構造

## 技術スタック

- Next.js 14 (App Router)
- TypeScript
- Tailwind CSS
- React

## セットアップ

```bash
# 依存関係のインストール
npm install

# 開発サーバーの起動
npm run dev
```

ブラウザで [http://localhost:3000](http://localhost:3000) を開いて確認してください。

## プロジェクト構造

```
├── app/
│   ├── layout.tsx      # ルートレイアウト
│   ├── page.tsx        # トップページ
│   └── globals.css     # グローバルスタイル
├── components/
│   ├── Header.tsx      # ヘッダー
│   ├── Footer.tsx      # フッター
│   ├── Hero.tsx        # ファーストビュー
│   ├── Features.tsx    # 3つの特長
│   ├── Concern.tsx     # 悩み共感ブロック
│   ├── Concept.tsx     # コンセプトセクション
│   ├── Product.tsx     # 商品セクション
│   ├── Ingredients.tsx # 成分・設計思想
│   ├── Story.tsx       # ブランドストーリー
│   ├── Topics.tsx      # Topics/News
│   └── Information.tsx # Information
└── package.json
```

## デザイン方針

- **背景**: 白〜淡いベージュ系
- **フォント**: Noto Sans JP / Noto Serif JP（細め・上品）
- **色数**: 3色以内（ブランドカラー＋グレー＋白）
- **文字量**: 最小限
- **CTA**: 目立たせすぎない（1ページ1〜2箇所）

## ブランドカラー

- Beige: `#F5F3F0`
- Cream: `#FAF8F5`
- Brown: `#8B7355`
- Dark: `#5C4A3A`
