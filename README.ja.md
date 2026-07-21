<div align="center">

# Design PPT

**情報を箱に詰めるのではなく、設計されたプレゼンテーションを作るための Agent Skill。**

[English](README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

</div>

![Design PPT — エディトリアルなプレゼンテーションシステム](assets/readme/hero.png)

Design PPT は、素材を洗練された一貫性のあるプレゼンテーションへ変換する、ポータブルな Agent Skill です。ストーリー設計、ビジュアル方針、目的別レイアウト、制作ルール、レンダリング QA を標準的な `SKILL.md` パッケージにまとめています。

Open Design、MCP サーバー、daemon、専用デザインアプリは**不要**です。

## 主な機能

- **スライドより先にストーリーを設計**：対象者、主張、根拠、求める行動を最初に定義します。
- **結論を示すタイトル**：単なるトピック名ではなく、そのページで伝える結論をタイトルにします。
- **一つのデザインシステム**：書体、色、余白、画像、チャート、図形のルールを統一します。
- **目的に応じたレイアウト**：ステートメント、根拠、比較、プロセス、システム、事例、引用、表を使い分けます。
- **AI スライド特有の癖を抑制**：カードの乱用、小さな文字、意味のないグラデーション、ピル型ラベル、弱いコントラストを避けます。
- **レンダリングによる QA**：実際のピクセルを確認し、はみ出し、切れ、階層、リズム、一貫性を修正します。
- **正直な出力モード**：編集可能な PPTX を優先し、必要な場合だけ画像ベース PPTX、PPTX ツールがない場合は HTML を使用します。

## 出力例

以下は、外部フォント、画像、プレゼンテーションサービスを使わず、同梱 HTML テンプレートだけで行ったフォワードテストの結果です。

| 表紙 | 比較 | プロセス |
|:---:|:---:|:---:|
| ![エディトリアルな表紙](assets/readme/example-cover.png) | ![比較スライド](assets/readme/example-comparison.png) | ![プロセススライド](assets/readme/example-process.png) |

## インストール

### Agent にインストールさせる（推奨）

Codex では次のように依頼します。

```text
Use $skill-installer to install and validate the skill from:
https://github.com/zuomian726/design-ppt
```

その他の Agent Skills 対応 Agent では：

```text
Install https://github.com/zuomian726/design-ppt as an Agent Skill.
Place the repository root in the configured skills directory and verify SKILL.md.
```

### Codex に手動インストール

```bash
git clone https://github.com/zuomian726/design-ppt.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/design-ppt"
```

インストール後、Codex を再起動するか新しいタスクを開始してください。

### 更新

```bash
git -C "${CODEX_HOME:-$HOME/.codex}/skills/design-ppt" pull --ff-only
```

## 使い方

厳密なデザインルールを適用したい場合は `$design-ppt` を明示します。

```text
Use $design-ppt to turn the attached strategy document into a
12-slide editable executive PPTX for the leadership team.
Use a restrained, editorial, high-contrast visual direction.
```

```text
Use $design-ppt to redesign this existing deck without changing
facts or data. Keep it editable and return PPTX plus a PDF preview.
```

```text
Use $design-ppt to create a Japanese/English bilingual investor deck
with message titles, accurate charts, and varied visual rhythm.
```

PPT/PPTX の作成・再設計、ピッチデック、経営会議資料、キーノート、HTML デックなどの依頼では、自動的に起動することもできます。

## 仕組み

```text
素材
  ↓
対象者 + 主張 + 根拠
  ↓
1 ページ 1 結論のスライドマップ
  ↓
書体 + 色 + グリッド + 画像システム
  ↓
ネイティブ PPTX または固定キャンバス HTML
  ↓
レンダー → 確認 → 修正 → 納品
```

コアのビジュアルルールは常に読み込み、デックの新規設計や再構成時にはストーリー／レイアウト資料を、制作・書き出し前には production／QA 資料を追加で読み込みます。

## 出力モード

| モード | 適した用途 | 編集性 | 再現性 |
|---|---|---:|---:|
| ネイティブ PPTX | 共同編集、経営レビュー、定期レポート | 高 | 高（ビューアー依存） |
| 画像ベース PPTX | キーノート、発表会、最終ビジュアル | 低 | 非常に高い |
| 自己完結 HTML | ブラウザ配信、PPTX ツールがない環境 | ソース編集可 | ブラウザ上で非常に高い |

HTML、PDF、スライド画像を編集可能な PPTX として扱うことはありません。

## 要件と互換性

- Agent Skills / `SKILL.md` ディレクトリに対応する Agent。
- 編集可能な PPTX には、Agent 側のプレゼンテーションツールが必要です。
- ビジュアル QA にはブラウザまたはプレゼンテーションレンダラーを推奨します。
- API Key、MCP、daemon、デスクトップデザインアプリは必須ではありません。

Codex で検証およびフォワードテスト済みです。他の互換 Agent でも同じファイルを利用できますが、最終的な出力形式は Agent 自身の制作・レンダリング能力によって決まります。

## リポジトリ構成

```text
design-ppt/
├── SKILL.md                         # トリガーと実行フロー
├── agents/openai.yaml              # Codex UI メタデータ
├── references/
│   ├── design-rules.md             # ビジュアル品質基準
│   ├── story-and-layouts.md         # ストーリーと目的別レイアウト
│   └── production-and-qa.md        # 制作・レンダー・書き出し検証
└── assets/
    ├── html-deck/index.html        # 依存なしの HTML フォールバック
    └── readme/                     # README 用画像と出力例
```

## デザイン原則

1. 1 スライドにつき、一つの結論と一つの焦点。
2. コンテナや装飾より、構図と余白を優先。
3. ストックアイコンより、実際の根拠を優先。
4. デック全体は一貫させ、ページの流れには変化をつける。
5. 納品前に、必ずレンダリング結果を確認する。
6. 編集性と書き出し方式のトレードオフを明示する。

## ライセンス

[MIT](LICENSE)
