# GitHub へのアップロード方法

## 1. 事前準備

- **GitHub アカウント**を作成していない場合は [github.com](https://github.com) で作成
- **Git** がパソコンにインストールされているか確認（ターミナルで `git --version`）

---

## 2. GitHub で新しいリポジトリを作る

1. GitHub にログイン → 右上の **+** → **New repository**
2. **Repository name**: 例）`tsuhan-hyakka`（任意の名前）
3. **Public** を選択
4. **「Add a README file」はチェックしない**（すでにローカルにファイルがあるため）
5. **Create repository** をクリック
6. 作成後、表示される **リポジトリのURL** をコピー（例: `https://github.com/あなたのユーザー名/tsuhan-hyakka.git`）

---

## 3. ローカルで Git を初期化してプッシュする

ターミナル（または Cursor のターミナル）で、**このプロジェクトのフォルダ**に移動してから、次のコマンドを順に実行します。

```bash
# プロジェクトフォルダに移動（パスはあなたの環境に合わせて変更）
cd "/Users/hohoemibiyou/Desktop/AIカーソル/通販pj"

# Git の初期化（まだやっていない場合）
git init

# すべてのファイルをステージング（images フォルダも含む）
git add .

# 初回コミット
git commit -m "初回：百花ジェル通販サイト"

# メインブランチの名前を main に（必要な場合）
git branch -M main

# GitHub のリポジトリを「リモート」として追加（URL はあなたのリポジトリに書き換え）
git remote add origin https://github.com/あなたのユーザー名/リポジトリ名.git

# プッシュ（アップロード）
git push -u origin main
```

- **ユーザー名・リポジトリ名** は、手順2で作ったリポジトリのURLに合わせて書き換えてください。
- 初回の `git push` で GitHub の **ユーザー名** と **パスワード（または Personal Access Token）** を聞かれたら入力します。パスワードは通常ログイン用ではなく、**Personal Access Token** を使います（GitHub → Settings → Developer settings → Personal access tokens で発行）。

---

## 4. 画像（images フォルダ）について

- **このプロジェクトでは `images` フォルダは .gitignore に入っていません。**
- そのため `git add .` で **画像ファイルも一緒に GitHub にアップロードされます。**
- 画像が「反映されない」と感じる場合は、次の点を確認してください。

### 画像が反映されない場合の確認

1. **ファイルがコミットに含まれているか**
   - `git status` で `images/` 以下のファイルが表示されるか確認
   - 表示されない場合は `git add images/` で追加してから `git commit` と `git push`

2. **GitHub Pages で公開している場合**
   - HTML では `./images/〇〇.png` のように相対パスで参照しているため、リポジトリのルートで公開していれば画像は表示されます。
   - GitHub Pages の設定：リポジトリの **Settings** → **Pages** → Source を **main** ブランチに設定。

3. **画像が大きすぎる場合**
   - GitHub は 1 ファイル 100MB まで。それを超える場合は [Git LFS](https://git-lfs.github.com/) の利用を検討。

---

## 5. images フォルダの「作成方法」（別PCでクローンしたときなど）

ほかの人や別のPCで `git clone` した場合は、**images フォルダと中身も一緒に取得**されます。手動で「フォルダだけ作る」必要はありません。

もし **画像なしでリポジトリだけ配布** したい場合は、次のようにできます。

### 方法A：空の images フォルダを残す

```bash
# images フォルダを空にして、中身だけ .gitignore に追加する場合は
# .gitignore に以下を追加:
# /images/*
# !/images/.gitkeep
# そして images フォルダに空の .gitkeep ファイルを作成
touch images/.gitkeep
git add images/.gitkeep
git commit -m "images フォルダを保持"
```

### 方法B：必要な画像リストを README に書く

`README.md` に「このサイトで使う画像は次のファイルを images に入れてください」と一覧を書いておくと、クローンした人が画像を用意しやすくなります。  
このプロジェクトで参照している主な画像は次のとおりです。

- `brand-about.png`
- `carousel-1.png` ～ `carousel-4.png`, `carousel-family.png`, `carousel-kiso.png`
- `clinic-explanation.png`, `clinic-treatment.png`, `clinic-hyakkaryoran.png`
- `hero-banner.png`, `hero-full.png`
- `product-detail.png`, `product-hero.png`, `product-main.png`
- その他 `images/` 内の PNG ファイル

---

## 6. 2回目以降の更新の流れ

コードや画像を直したあと、GitHub に反映する手順です。

```bash
cd "/Users/hohoemibiyou/Desktop/AIカーソル/通販pj"
git add .
git commit -m "〇〇を変更（メッセージは自由）"
git push
```

---

## まとめ

| やりたいこと           | 手順 |
|------------------------|------|
| 初めて GitHub に上げる | 2 でリポジトリ作成 → 3 のコマンドを順に実行 |
| 画像も一緒に上げる     | `git add .` で images も含まれる（そのままでOK） |
| 画像フォルダだけ用意   | 通常は clone で images も取れる。空で残すなら 5 の方法A |
| あとから更新する       | 6 の「2回目以降の更新の流れ」 |

不明な点があれば、どの段階で詰まっているか（例：リポジトリ作成、git push、GitHub Pages で画像が出ない など）を教えてもらえれば、そこだけ詳しく説明できます。
