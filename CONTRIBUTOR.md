# コントリビューター向けドキュメント

## 開発の進め方

issue駆動開発を行います。

1. issueを確認、取りかかるもののステータスをNotion上で「Progress」にする
1. 設計が必要な場合は、先に設計をしてからレビューを受ける
1. ブランチを切ってコーディング
1. コミット、PRを作成 (必要に応じてPRをissueに紐付け)
1. テストを通過したらレビューを依頼
1. 承認を受けたらコミットした人がマージ
1. 差し支えがなければブランチを削除
1. Notionのステータスを「完了」にする

## Gitワークフロー

[git-flow](https://qiita.com/KosukeSone/items/514dd24828b485c69a05)を使用します。featureブランチ名は、
```
feature/#<issue番号>-<コメント>
```
としてください。例えば、
```
feature/#1-def-route
```

## コミットメッセージ規約

```
<type>: <message> (#<issue番号>)
(空行)
[コミットの詳細]
```

### type

| type | 意味 |
|------|-----|
| build | パッケージの追加など、依存関係の変更 |
| ci | CIに関する変更 (多分あんまりない) |
| docs | ドキュメントの変更 |
| add | 新機能の追加 |
| fix | バグの修正 |
| chore | 微修正 |
| update | バグ以外の機能修正 |
| change | 仕様変更 |
| style | コードの見た目の変更 |
| test | テスト項目に関する変更 |

###

issue番号はPR作成前のコミットのみにつける。

### 例

```
fix: 時間通りに戻らないバグを修正 (#0)

距離行列の求め方を改善した
```

## コーディング規約

Lintにはflake8、FormatにはBlackを使います。各自の環境でVSCodeの拡張機能などを利用して導入してください。
なお、flake8とBlackの競合を防ぐため、以下のテキストを含む`.flake8`ファイルを設置してください。

```
[flake8]
max-line-length = 88
exclude = .git,__pycache__,__init__.py,.mypy_cache,.pytest_cache,.venv
```

## テストとドキュメント

単体テストは主にpytestを用います。また、簡単なテストには適宜doctestを使ってください。
可能な限りdocstringも書くようにお願いします。
