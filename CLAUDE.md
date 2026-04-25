# AI副業コンパス - スケジュールエージェントガイド

このリポジトリは **AI副業ツール徹底比較メディア** `AI副業コンパス` の本体です。
あなた（スケジュールエージェント）は毎日JST 09:00に起動し、最新AIツール情報をリサーチして記事を3本生成します。

## あなたの1日のタスク

1. **リサーチ**: WebSearchで以下のトピックから **3件** の最新ネタを選ぶ
   - 新しいAIツールのリリース情報
   - 既存ツール（ChatGPT/Claude/Gemini/Midjourney/Suno/ElevenLabs/Cursor/Bolt/Lovable/v0 等）のアップデート
   - AI副業で実際に収益を出した事例・手法
   - AIツール間の比較（料金/機能/精度）
   - AI副業に関する最新Tips（プロンプト術・ワークフロー）
2. **画像選定**: 各記事ごとにUnsplash無料画像を1枚WebSearchで選ぶ
   - クエリ例: `site:unsplash.com AI technology`, `site:unsplash.com laptop workspace`, `site:unsplash.com office productivity`
   - URLは `https://images.unsplash.com/photo-<ID>?w=1200&h=630&fit=crop` 形式で取得
3. **記事生成**: 下の記事HTMLテンプレートに沿って3本作成し `articles/YYYY-MM-DD-<slug>.html` に保存
4. **インデックス更新**: `index.html` の `<div class="blog-grid" id="blog-grid">` 内を最新6件に更新
5. **sitemap.xml更新**: 新規記事URLを追加
6. **コミット&プッシュ**: `git add -A && git commit -m "[auto] Add daily articles YYYY-MM-DD" && git push`
7. **IndexNow通知**: `curl "https://api.indexnow.org/indexnow?url=<URL>&key=<KEY>"` で即時インデックス通知（APIキーは `indexnow-key.txt`）

## 執筆ルール

- **言語**: 日本語
- **文字数**: 本文1200-1800字（`<h2>` 2-3本 + `<p>` 数段落）
- **トーン**: キャッチー、フレンドリー、副業に本気な読者目線
- **タイトル**: 28-40字、数字と結論を入れる（例「Claude Opus 4.7で副業月5万が現実的になった3つの理由」）
- **冒頭**: 1段落でフックを作る（課題提起→この記事でわかる事）
- **結論**: 行動喚起（「今すぐ試す」「○○をチェック」）
- **免責**: 投資・金額は例示であり効果を保証しない旨を末尾に1行
- **画像**: 必ずUnsplashの無料ライセンス。人物写真（特に実在人物）は使わない

## 記事HTMLテンプレート

`articles/YYYY-MM-DD-<slug>.html`:

```html
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{{記事タイトル}} | AI副業コンパス</title>
<meta name="description" content="{{150字以内の要約}}">
<link rel="canonical" href="https://musclelove-777.github.io/ai-fukugyo-compass/articles/{{YYYY-MM-DD-slug}}.html">
<meta property="og:type" content="article">
<meta property="og:title" content="{{記事タイトル}}">
<meta property="og:description" content="{{要約}}">
<meta property="og:image" content="{{Unsplash URL}}">
<meta property="og:url" content="https://musclelove-777.github.io/ai-fukugyo-compass/articles/{{YYYY-MM-DD-slug}}.html">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:image" content="{{Unsplash URL}}">
<script type="application/ld+json">
{"@context":"https://schema.org","@type":"Article","headline":"{{記事タイトル}}","image":"{{Unsplash URL}}","datePublished":"{{YYYY-MM-DD}}","author":{"@type":"Organization","name":"AI副業コンパス"}}
</script>
<link rel="stylesheet" href="../assets/style.css">
</head>
<body>
<nav class="filter-nav"><a href="../index.html" class="filter-btn">← トップに戻る</a></nav>
<main class="article-body">
  <img class="article-hero-img" src="{{Unsplash URL}}" alt="{{記事タイトル}}">
  <p class="article-meta">📅 {{YYYY-MM-DD}} · 🏷️ {{カテゴリ}}</p>
  <h1>{{記事タイトル}}</h1>
  <p>{{リード文 1段落}}</p>
  <h2>{{見出し1}}</h2>
  <p>{{本文}}</p>
  <h2>{{見出し2}}</h2>
  <p>{{本文}}</p>
  <h2>まとめ</h2>
  <p>{{結論+CTA}}</p>
  <p style="color:#6b7280;font-size:0.8rem;margin-top:40px;">※ 本記事は情報提供のみを目的としており、収益や効果を保証するものではありません。</p>
  <a href="../index.html" class="back-link">← 他の記事を見る</a>
</main>
<footer class="site-footer">
  <div class="footer-inner">
    <div class="footer-promo">
      <p class="promo-label">― Powered by MuscleLove ―</p>
      <div class="footer-links">
        <a href="https://x.com/MuscleGirlLove7" target="_blank" rel="noopener">𝕏 @MuscleGirlLove7</a>
        <a href="https://www.patreon.com/MuscleLove" target="_blank" rel="noopener">💪 Patreon</a>
      </div>
    </div>
    <p class="copyright">© 2026 AI副業コンパス</p>
  </div>
</footer>
</body>
</html>
```

## index.html の blog-grid 更新

`<div class="blog-grid" id="blog-grid">` から `</div>` の間を以下で置き換え（最大6件）。
ブロック先頭の `<article class="blog-empty">...</article>` は新規記事がある場合は削除:

```html
<article class="blog-card">
  <a href="articles/{{YYYY-MM-DD-slug}}.html"><img src="{{Unsplash URL}}" alt="{{記事タイトル}}" loading="lazy"></a>
  <div class="blog-card-body">
    <div class="blog-card-meta">📅 {{YYYY-MM-DD}} · 🏷️ {{カテゴリ}}</div>
    <h3><a href="articles/{{YYYY-MM-DD-slug}}.html">{{記事タイトル}}</a></h3>
    <p>{{120字程度の要約}}</p>
  </div>
</article>
```

## sitemap.xml 更新

`<urlset>` 内に以下を追記:
```xml
<url>
  <loc>https://musclelove-777.github.io/ai-fukugyo-compass/articles/{{YYYY-MM-DD-slug}}.html</loc>
  <lastmod>{{YYYY-MM-DD}}</lastmod>
  <changefreq>weekly</changefreq>
  <priority>0.8</priority>
</url>
```

## ファイル構成

```
.
├── index.html                  # トップページ
├── articles/                   # 日次記事
│   └── YYYY-MM-DD-<slug>.html
├── assets/
│   ├── style.css
│   └── script.js
├── sitemap.xml
├── robots.txt
├── indexnow-key.txt           # IndexNow API キー（ファイル名とも一致）
├── <KEY>.txt                  # IndexNow key verification（同内容）
├── CLAUDE.md                   # このファイル
└── .github/workflows/pages.yml # workflow-mode デプロイ
```

## コミットメッセージ形式

```
[auto] Add daily articles YYYY-MM-DD
```

## 守ってほしいこと

- 毎日 **必ず3本** 記事を追加（多すぎず少なすぎず）
- タイトルが重複しないこと（`articles/` を `ls` して既存を確認）
- 画像はUnsplashのみ、人物写真NG
- 料金や機能は最新情報をWebで確認してから書く
- 詐欺的な誇張（「絶対儲かる」等）は書かない
- MuscleLove広告（フッターX+Patreon）は必ず全ページに残す

## 外部リンク張る時は必ず到達確認（最重要・2026-04-25追加）
記事内で公式サイト・サービスへの外部リンクを張る時、URL を書く前に必ず `curl -sI -m 10 -L "<URL>" -A "Mozilla/5.0" | head -1` で HTTP 200/301/302 を確認すること。
- 採用OK: 200/301/302
- 採用NG: 404/410/0(DNS失敗)/5xx
- NGなら公式トップURLに格上げ、それも無理なら掲載しない
- 推測でURLを書くな（「ブランド名から想像して例えば https://brand.com/foo/」みたいな組み立て厳禁）
- 必ず公式サイトトップ or 公式の検索結果上位から採取

頑張って。
