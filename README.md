# Zenn Contents（Fork Repository）

このリポジトリは、Zenn 記事を作成・レビューするための Fork リポジトリです。
記事はこのリポジトリ（origin）で管理し、Pull Request を通して upstream リポジトリへマージします。

実際の公開・同期は upstream 側で行います。

## 概要

- Zenn 記事を Markdown + Git で管理
- origin（Fork）で PR を作成し、upstream にマージ
- マージ前に ローカル preview で表示確認
- 個人記事 / Publication 記事どちらにも対応

## 基本的な流れ

- origin（この Fork）で記事を作成・編集
- ローカルで preview を確認
- origin → upstream に Pull Request を作成
- upstream でマージ

## 記事作成の手順（origin）

1. 記事を作成

```shell
npx zenn new:article
```

- articles/ 配下に Markdown ファイルが生成される
- ファイル名（slug）は自動生成
- slug は 記事 URL に使われるため変更しないこと

2. 記事を書く

```yaml
# フロントマターでタイトル、タグなど設定可能
---
title: "記事タイトル"
type: "tech"
topics: ["vue", "rust"]
published: false
---
```

- topic（タグ）は最大５つまで設定可能
- 下書きの場合 `published: false`　公開の場合は`true`に設定
  - 個人投稿の場合は`true`でマージして OK
  - publication で投稿する場合は`false`でマージしてレビュー完了後に`true`へ変更すること
  - publication に投稿する場合は`publication_name: "{publication名}"`を追加で記載

3. ローカル preview

- 記事を PR に出す前に、必ずローカルで表示確認を行うこと。

```shell
# preview 起動
npx zenn preview
```

- ブラウザで http://localhost:8000 が開く

- 以下をチェックします

  - 表示崩れがないか
  - 見出し構造が不自然でないか
  - コードブロック・画像が正しく表示されるか

- 軽微な修正でも preview 確認を推奨します

## 既存の Zenn 記事を Fork で管理する場合

Zenn の Web エディタで作成済みの記事も、この Fork に移管できます。

### 手順

- Zenn エディタから本文をコピー
- articles/ に Markdown ファイルを作成
- 既存記事と 同じ slug（ファイル名）、 フロントマターを使う
- published: false のまま commit
- slug が変わると 別記事扱い になるため注意
- Pull Request 運用（origin → upstream）

## PR 作成ルール

- PR は origin から upstream に作成
- 記事単位、もしくは関連する記事ごとにまとめる
- マージ前に preview 確認済みであること

## PR タイトル例

```shell
chore: add Zenn article (2026-01-01)
```

## PR 本文に書くこと（簡潔で OK）

- 変更した記事ファイル
- 新規 or 既存記事の修正
- 公開予定かどうか

## 公開ルール

### 個人投稿の場合

- upstream にマージ後
- Zenn に反映されて公開される

### Publication に投稿する場合

- フロントマターに以下を追加

```
publication_name: "{publication名}"
published: false
```

- Publication のメンバー権限が必要
- 記事のレビューは二人以上に LGTM をもらうこと
- 公開設定は upstream 側で行う
- origin では下書き・調整のみ

## 注意点

- slug（ファイル名）変更は禁止
- Publication の場合は origin 側で published: true にしない

## Zenn CLIについて

* [📘 How to use](https://zenn.dev/zenn/articles/zenn-cli-guide)
