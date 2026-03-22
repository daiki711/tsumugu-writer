# WordPress HTML出力仕様

STEP 7で使用するHTML変換ルール。
WordPress「テキスト」タブに貼り付けることを前提とした出力形式。

---

## 出力形式

### ファイル出力はしない
- チャット上にそのままテキストで出力する
- コードブロック（```html〜```）で囲む
- 先頭にメタコメントを付与する

### メタコメント形式
```html
<!--
■ 入稿情報
タイトル（h1）: {タイトル}
メインKW: {KW}
共起KW: {KW1}, {KW2}, {KW3}
文字数（本文のみ）: 約{X,XXX}字
CTA: {プロダクト名}（{X}箇所）

■ 入稿手順
1. WordPressの投稿編集画面を開く
2. 右上の「テキスト」タブに切り替える
3. このコードブロック内のHTMLをそのまま貼り付ける
4. 「ビジュアル」タブに切り替えて表示を確認する
5. アイキャッチ画像を設定する
6. カテゴリ・タグを設定する
7. 予約投稿または即時公開する
-->
```

---

## HTML変換ルール

### 見出し
```html
<!-- h1 -->
<h1>{タイトル}</h1>

<!-- h2 -->
<h2>{見出し}</h2>

<!-- h3 -->
<h3>{見出し}</h3>
```

### 段落
```html
<p>{本文テキスト}</p>
```

### 監修者情報ボックス（h1直後に挿入）
```html
<div style="background: #f8f9fa; border-left: 4px solid #667eea; border-radius: 0 8px 8px 0; padding: 20px 24px; margin: 24px 0 40px;">
  <p style="font-size: 13px; color: #666; margin: 0 0 8px; font-weight: bold;">【監修者情報】</p>
  <p style="font-size: 15px; font-weight: bold; margin: 0 0 4px;">塔筋 大樹（とうすじ だいき）</p>
  <p style="font-size: 13px; color: #444; margin: 0 0 8px;">株式会社Tsumugu 代表取締役</p>
  <p style="font-size: 13px; color: #555; margin: 0; line-height: 1.7;">リクルートにて10年以上、製造業・建設業を中心とした採用支援に従事。その後独立し、中小製造業専門の採用・組織コンサルとして伴走型支援を提供。支援実績：50社以上（従業員数10〜300名規模の製造業）</p>
</div>
```

### 塔筋さんの吹き出しコメント
```html
<div style="display: flex; align-items: flex-start; gap: 16px; background: #fff9f0; border: 2px solid #ffb347; border-radius: 12px; padding: 20px 24px; margin: 32px 0;">
  <div style="flex-shrink: 0; width: 56px; height: 56px; border-radius: 50%; background: #ffb347; display: flex; align-items: center; justify-content: center; font-size: 24px;">💬</div>
  <div>
    <p style="font-size: 13px; font-weight: bold; color: #e67e00; margin: 0 0 6px;">塔筋より</p>
    <p style="font-size: 14px; color: #333; margin: 0; line-height: 1.8;">{吹き出しコメント本文}</p>
  </div>
</div>
```

### CTAブロック
```html
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); border-radius: 12px; padding: 28px 32px; margin: 40px 0; text-align: center; color: white;">
  <p style="font-size: 18px; font-weight: bold; margin: 0 0 12px; line-height: 1.6;">{CTAの見出し文}</p>
  <p style="font-size: 14px; margin: 0 0 20px; opacity: 0.9; line-height: 1.7;">{CTAの説明文}</p>
  <a href="{URL}" style="display: inline-block; background: white; color: #764ba2; font-weight: bold; font-size: 16px; padding: 14px 32px; border-radius: 8px; text-decoration: none;">▶ {ボタンテキスト}</a>
</div>
```

### ハイライトボックス（重要ポイントのまとめ）
```html
<div style="background: #f0f4ff; border: 2px solid #667eea; border-radius: 8px; padding: 20px 24px; margin: 24px 0;">
  <p style="font-size: 14px; font-weight: bold; color: #667eea; margin: 0 0 12px;">📌 {ボックスのタイトル}</p>
  <ul style="margin: 0; padding-left: 20px; color: #333; font-size: 14px; line-height: 1.9;">
    <li>{項目1}</li>
    <li>{項目2}</li>
    <li>{項目3}</li>
  </ul>
</div>
```

### 表（テーブル）
```html
<table style="width: 100%; border-collapse: collapse; margin: 24px 0; font-size: 14px;">
  <thead>
    <tr style="background: #667eea; color: white;">
      <th style="padding: 12px 16px; text-align: left; border: 1px solid #ddd;">{列見出し1}</th>
      <th style="padding: 12px 16px; text-align: left; border: 1px solid #ddd;">{列見出し2}</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background: white;">
      <td style="padding: 12px 16px; border: 1px solid #ddd;">{値1}</td>
      <td style="padding: 12px 16px; border: 1px solid #ddd;">{値2}</td>
    </tr>
    <tr style="background: #f8f9fa;">
      <td style="padding: 12px 16px; border: 1px solid #ddd;">{値3}</td>
      <td style="padding: 12px 16px; border: 1px solid #ddd;">{値4}</td>
    </tr>
  </tbody>
</table>
```

### 内部リンク（blockquote形式）
```html
<blockquote style="border-left: 4px solid #667eea; background: #f8f9ff; margin: 24px 0; padding: 16px 20px; border-radius: 0 8px 8px 0;">
  <p style="margin: 0 0 6px; font-size: 13px; color: #667eea; font-weight: bold;">📖 関連記事</p>
  <a href="{記事URL}" style="font-size: 14px; color: #333; text-decoration: none; font-weight: bold;">{記事タイトル}</a>
</blockquote>
```

### 番号付きリスト
```html
<ol style="padding-left: 20px; margin: 16px 0; font-size: 14px; line-height: 1.9; color: #333;">
  <li style="margin-bottom: 8px;">{項目1}</li>
  <li style="margin-bottom: 8px;">{項目2}</li>
</ol>
```

### 箇条書きリスト
```html
<ul style="padding-left: 20px; margin: 16px 0; font-size: 14px; line-height: 1.9; color: #333;">
  <li style="margin-bottom: 8px;">{項目1}</li>
  <li style="margin-bottom: 8px;">{項目2}</li>
</ul>
```

### 太字・強調
```html
<strong style="color: #333; font-weight: bold;">{強調テキスト}</strong>
```

---

## 出力サンプル構造

```html
<!--
■ 入稿情報
タイトル（h1）: 中小製造業の新卒採用を成功させる7つのポイント
メインKW: 中小製造業 新卒採用
共起KW: 採用ミスマッチ, 内定辞退 防ぐ, 工場見学, 求人票 書き方
文字数（本文のみ）: 約5,800字
CTA: マイナビ新卒（4箇所）

■ 入稿手順
1. WordPressの投稿編集画面を開く
2. 右上の「テキスト」タブに切り替える
3. このコードブロック内のHTMLをそのまま貼り付ける
4. 「ビジュアル」タブに切り替えて表示を確認する
5. アイキャッチ画像を設定する
6. カテゴリ・タグを設定する
7. 予約投稿または即時公開する
-->

<h1>中小製造業の新卒採用を成功させる7つのポイント【採用担当者向け】</h1>

<div style="background: #f8f9fa; border-left: 4px solid #667eea; ...">
  <!-- 監修者情報ボックス -->
</div>

<p>毎年新卒採用に挑戦しているのに、なかなか採用目標を達成できない。そんな中小製造業の人事担当者に向けて...</p>

<!-- 以下、本文続く -->
```
