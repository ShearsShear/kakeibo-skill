# kakeibo-skill

Claude Code用の家計簿管理スキル。支出の記録・分析と予算超過の判定を行います。

## 機能

- 支出の記録（テキスト入力対応）
- 予算状況の確認（消化率・超過警告）
- カテゴリ別の締め日サイクル管理
- 予算超過時の理由ヒアリング・記録
- カスタムカテゴリの設定

## インストール

### 1. スキルファイルをコピー

`.claude/skills/SKILL.md` をプロジェクトの `.claude/skills/` ディレクトリにコピーします。

```bash
mkdir -p .claude/skills
cp kakeibo-skill/.claude/skills/SKILL.md .claude/skills/
```

### 2. データディレクトリをセットアップ

`templates/` のCSVファイルを `kakeibo/` ディレクトリにコピーします。

```bash
mkdir -p kakeibo
cp kakeibo-skill/templates/*.csv kakeibo/
```

## 使い方

### スキルの呼び出し

```
/kakeibo
```

または「家計簿」「支出を記録」「予算確認」と入力

### 支出の記録

テキストで入力できます：

```
楽天カード 5000円
家賃 90000円
```

### 締め日の設定

カード会社ごとに締め日が異なる場合、`categories.csv` で設定できます：

```csv
category,description,closing_day
楽天カード,楽天カードでの支払い,12
PayPay,PayPayでの支払い,末日
```

## ファイル構成

```
kakeibo/
├── categories.csv  # カテゴリ設定（締め日含む）
├── budgets.csv     # 月額予算設定
├── expenses.csv    # 支出記録
└── overages.csv    # 超過理由の記録
```

## カスタマイズ

### カテゴリの追加

`categories.csv` を編集してカテゴリを追加できます。

### 予算の設定

`budgets.csv` を編集するか、`/kakeibo` から「予算を設定」を選択します。

## ライセンス

MIT License
