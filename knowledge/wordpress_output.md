# WordPress入稿用HTML出力ルール

## 概要
Writer Agentが記事本文を書いた後、このルールに従ってWordPress入稿可能なHTMLに変換する。
WordPressの「テキストエディター（HTMLモード）」に貼るだけで使える状態にすること。
ファイルへの保存はしない。チャット上にコードブロック（```html〜```）で囲んで出力する。

---

## 要素別変換ルール

### 見出し
```html
<h2>h2見出し</h2>
<h3>h3見出し</h3>
```

### 段落
```html
<p>通常テキスト</p>
<strong>太字</strong>
```

### 監修者情報ボックス（h1直後に挿入）
```html
<div class="supervisor-box">
  <table>
    <tr><td><strong>【監修者】 株式会社Tsumugu 代表　塔筋 大樹</strong></td></tr>
    <tr><td>リクルートを経て、2023年よりアド・イーグルHD役員として営業・企画・人事を管掌。同年、株式会社Tsumuguを設立。10年以上の経験を通じたHR領域のプロとして、「お客様と伴走する人材コンサル」を展開している。</td></tr>
  </table>
</div>
```

### 塔筋さんの吹き出し
```html
<div style="display:flex; align-items:flex-start; gap:12px; margin:20px 0; padding:16px; background:#fafafa; border-radius:8px;">
  <div style="font-weight:bold; min-width:80px; font-size:0.85em; color:#555;">塔筋 大樹</div>
  <div style="border-left:3px solid #ccc; padding-left:12px;">{コメント内容}</div>
</div>
```

### CTAブロック
```html
<div style="background:#f0f8ff; border-left:4px solid #4A90D9; padding:20px; margin:30px 0; border-radius:4px;">
  <p style="font-weight:bold; font-size:1.1em; margin-bottom:10px;">{キャッチコピー}</p>
  <a href="{URL}" style="display:inline-block; background:#4A90D9; color:#fff; padding:12px 24px; border-radius:4px; text-decoration:none; font-weight:bold;">{ボタンテキスト}</a>
</div>
```

### ハイライトボックス
```html
<div style="background:#f9f9f9; border:1px solid #ddd; border-radius:6px; padding:20px; margin:20px 0;">
  <p style="font-weight:bold; margin-bottom:12px;">{ボックスタイトル}</p>
  <ul style="margin:0; padding-left:20px;">
    <li style="margin-bottom:6px;">{項目}</li>
  </ul>
</div>
```

### 内部リンク
```html
<blockquote><a href="{URL}">{記事タイトル}</a></blockquote>
```

### 表（テーブル）
```html
<table style="width:100%; border-collapse:collapse; font-size:14px;">
  <thead>
    <tr style="background:#4A90D9; color:#fff;">
      <th style="padding:10px; border:1px solid #ddd;">{列見出し}</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:10px; border:1px solid #ddd;">{値}</td></tr>
  </tbody>
</table>
```

---

## WordPress入稿手順
1. WordPress管理画面 → 投稿 → 新規追加
2. タイトル欄にh1テキストを入力
3. 本文エディタ右上の「テキスト」タブをクリック
4. コードブロックの内容をすべて貼り付け
5. カテゴリ・タグ・アイキャッチ画像を設定
6. プレビューで確認後、公開
