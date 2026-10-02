# Fantasy Novel Worldbuilding Repository

このリポジトリでは、ファンタジー小説の世界観・登場人物・地理・魔法体系・物語構成などをMarkdownで管理する。

設定資料と物語本編を分離し、設定変更や追加があった場合でも追跡しやすい構成を採用する。

---

## Directory Structure

基本構成は以下とする。

```text
.
├─ README.md
│
├─ world/
│  ├─ overview.md
│  ├─ history.md
│  ├─ calendar.md
│  ├─ religion.md
│  └─ culture.md
│
├─ locations/
│  ├─ world-map.md
│  ├─ kingdoms/
│  └─ cities/
│
├─ characters/
│  └─ README.md
│
├─ factions/
│
├─ magic/
│  ├─ overview.md
│  ├─ rules.md
│  ├─ spells.md
│  └─ artifacts.md
│
├─ creatures/
│
├─ story/
│  ├─ premise.md
│  ├─ timeline.md
│  ├─ plot.md
│  ├─ chapters/
│  └─ unresolved.md
│
├─ reference/
│  ├─ glossary.md
│  ├─ names.md
│  └─ chronology.md
│
├─ notes/
│  ├─ ideas.md
│  ├─ questions.md
│  └─ discarded.md
│
└─ assets/
   ├─ maps/
   └─ images/
```

最初からすべてのディレクトリを使用する必要はない。

初期段階では以下を中心に使用し、設定量の増加に応じて分割する。

```text
README.md
characters/
world/
locations/
story/
notes/
```

---

# Repository Rules

## 1. 設定と物語を分離する

世界そのものの設定と、作中で起こる出来事を分けて管理する。

### Setting

以下には「この世界において何が存在し、どのようなルールになっているか」を記述する。

```text
world/
locations/
characters/
factions/
magic/
creatures/
reference/
```

### Story

以下には「物語の中で何が起こるか」を記述する。

```text
story/
```

例：

- 魔法がどのような原理で使えるか → `magic/`
- 主人公が第3章で魔法を習得する → `story/`
- 王国が過去に戦争を経験した → `world/history.md`
- その戦争の真相が第8章で判明する → `story/`

---

## 2. 1つの主要設定につき1ファイルを基本とする

人物、国家、都市、組織など、独立した設定は可能な限り個別ファイルに分ける。

例：

```text
characters/
├─ albert.md
├─ alice.md
└─ leon.md
```

```text
locations/
└─ kingdoms/
   ├─ astoria.md
   └─ valeria.md
```

設定が少ないうちは1ファイルにまとめてもよい。

内容が増えて読みづらくなった段階で分割する。

---

## 3. ファイル名は原則として英数字を使用する

ファイル名・ディレクトリ名は基本的に以下の形式とする。

```text
lowercase-kebab-case.md
```

例：

```text
royal-family.md
magic-academy.md
ancient-dragon.md
```

本文中の名称は日本語で記述してよい。

---

## 4. Canon Status を設定する

設定には、その内容がどの程度確定しているかを示す `status` を記述する。

Markdownファイルの冒頭にFront Matterを記述する。

```yaml
---
status: canon
updated: 2026-10-02
---
```

使用するステータスは以下とする。

### `idea`

思いつき段階。

まだ正式設定として採用していない。

### `draft`

採用する可能性が高いが、内容が確定していない。

### `canon`

正式設定。

原則として現在の作品世界における正しい設定として扱う。

### `deprecated`

過去に使用していたが、現在は採用していない設定。

削除せず、必要に応じて変更履歴として残す。

---

## 5. Canon と Idea を混同しない

思いついた設定をそのまま正式設定として扱わない。

未確定の内容は必ず、

```yaml
status: idea
```

または、

```yaml
status: draft
```

とする。

物語を書く際の基準として使用してよいのは、原則として `canon` の設定とする。

---

## 6. 人物設定は共通フォーマットを使用する

人物ファイルは原則として以下の構造を使用する。

```md
---
status: draft
updated: YYYY-MM-DD
---

# 名前

## 基本情報

- 年齢:
- 性別:
- 出身:
- 所属:
- 職業:

## 外見

## 性格

## 能力

## 生い立ち

## 目的

## 人間関係

## 作中での役割

## 秘密

## メモ
```

不要な項目は省略してよい。

必要になった項目は自由に追加してよい。

---

## 7. README.md は目次として使用する

ルートの `README.md` は、リポジトリ全体の入口として使用する。

重要な設定ファイルへのリンクを掲載する。

設定が増えた場合、各ディレクトリにも `README.md` を配置して目次を作成してよい。

例：

```text
characters/
├─ README.md
├─ albert.md
├─ alice.md
└─ leon.md
```

---

## 8. 関連設定はMarkdownリンクで接続する

関連する設定同士は、可能な限りMarkdownリンクで接続する。

例：

```md
アルベルトは[アストリア王国](../locations/kingdoms/astoria.md)の騎士である。
```

人物と組織、都市と国家、魔法と歴史など、関連する設定をリンクすることで設定を追いやすくする。

---

## 9. 用語集を作成する

重要な固有名詞や設定は `reference/glossary.md` にまとめる。

例：

```md
# 用語集

## アストリア

北方に存在する王国。

→ [詳細](../locations/kingdoms/astoria.md)

## 魔晶石

魔力を蓄積する特殊な鉱物。

→ [詳細](../magic/artifacts.md)

## 聖教会

大陸最大規模の宗教組織。

→ [詳細](../factions/church.md)
```

用語集は詳細設定を書く場所ではなく、設定を探すための索引として使用する。

---

## 10. 時系列は一元管理する

世界史や物語上の出来事について、時間関係が重要なものは時系列として管理する。

主に以下を使用する。

```text
world/history.md
reference/chronology.md
story/timeline.md
```

役割は以下のように分ける。

### `world/history.md`

世界の歴史そのもの。

### `reference/chronology.md`

歴史上の出来事を年代順に確認するための一覧。

### `story/timeline.md`

物語開始後に起こる出来事の時系列。

---

## 11. 未解決設定を残す

決める必要があるが、まだ結論が出ていない事項は、

```text
story/unresolved.md
```

または、

```text
notes/questions.md
```

に記録する。

設定の矛盾に気づいた場合も、その場で無理に決定せず未解決事項として記録してよい。

---

## 12. アイデアを捨てない

採用前のアイデアは、

```text
notes/ideas.md
```

採用しなかった案は、

```text
notes/discarded.md
```

に残す。

採用しなかった設定でも、別の人物・地域・作品で再利用できる可能性があるため、原則として完全削除しない。

---

## 13. 画像は assets に保存する

地図、人物参考画像、紋章などの画像は `assets/` 以下に保存する。

```text
assets/
├─ maps/
└─ images/
```

設定Markdownから相対パスで参照する。

---

# Main Index

## 世界観

- [世界概要](world/overview.md)
- [システムの五層構造](world/system.md)
- [世界の歴史と存続](world/history.md)
- [現実時間と世界時間](world/time.md)
- [生物AI・出生・成長・死](world/life.md)
- [世界管理AI](world/management-ai.md)
- [神と宗教](world/religion.md)
- [外部入出力と神託の水晶](world/external-interface.md)
- [バグと異常現象](world/anomalies.md)

## 地理・魔法

- [世界の端](locations/world-edge.md)
- [魔法体系](magic/overview.md)

## ストーリー

- [物語概要とテーマ](story/premise.md)
- [全体プロット](story/plot.md)
- [物語時系列](story/timeline.md)
- [第一章：世界の外を夢想した者](story/chapters/chapter-01.md)
- [第二章：書物を継ぐ者](story/chapters/chapter-02.md)
- [第三章：外を見る者](story/chapters/chapter-03.md)
- [物語の未解決事項](story/unresolved.md)

## リファレンス・メモ

- [用語集](reference/glossary.md)
- [年代記](reference/chronology.md)
- [短編・サブストーリー案](notes/ideas.md)
- [世界設定の検討事項](notes/questions.md)

---

# Git Rules

設定を大きく変更した場合は、変更理由が分かるコミットメッセージを付ける。

例：

```text
Add magic system basics
Add Astoria kingdom setting
Update Albert backstory
Change origin of magic
Deprecate old calendar system
```

正式設定を変更する場合は、可能な限り変更前の内容をGit履歴から追跡できる状態にする。

---

# Principle

このリポジトリの目的は、設定を増やすことそのものではない。

**物語を書く際に必要な情報を、矛盾なく簡単に参照できる状態にすること**を最優先とする。

そのため、

- 最初から細かく分類しすぎない
- 必要になった段階でファイルを分割する
- 未確定設定と正式設定を明確に分ける
- 関連設定をリンクする
- 古い設定もGit履歴から確認できるようにする

という方針で管理する。
