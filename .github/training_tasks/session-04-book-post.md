# セッション4: 書籍投稿フロー

## 目的
- `books` コレクションのモデルと CRUD を実装し、ユーザーがレビューを投稿できる状態をつくる。
- Cloud Functions（callable）を活用して `bookCount` の整合性を確保する。
- 投稿一覧画面を `CustomScrollView` + `SliverList` で構築し、リアクティブな表示を実現する。

## 作業項目
- [ ] `Book` モデルを `freezed` × `json_serializable` で定義し、Repository / UseCase 層を整備する。
- [ ] 書籍投稿フォーム（タイトル、説明、画像、URL）の UI とバリデーションを実装する。
- [ ] 画像アップロードを Profile の実装と共通化し、Storage への書き込みを行う。
- [ ] Cloud Functions プロジェクトを初期化し、Callable Function で書籍追加・削除を行う API を実装する。
- [ ] Callable Function 内で `users/{uid}/bookCount` をトランザクションで増減させる。
- [ ] 書籍投稿 UI から Cloud Functions を呼び出せるようにし、成功 / 失敗レスポンスのハンドリングを実装する。
- [ ] 自分の投稿一覧画面を実装し、`cratedAt` 降順で表示する。

## 実装時に意識できているといいこと
- なぜ `CustomScrollView` と `SliverList` を採用するのか、`ListView` や`SingleChildScrollView `の違いを整理してみよう。
- Callable Function でトランザクションを使う理由と、通常の `update` では問題が起こるケースを考えてみよう。

## 完了条件
- 書籍投稿が Firestore に保存され、一覧画面に即時反映される。
- 投稿編集・削除が Cloud Functions 経由で動作し、`bookCount` が正しく増減する。
- フォーム入力エラー時にユーザーへ適切なフィードバックが表示される。
