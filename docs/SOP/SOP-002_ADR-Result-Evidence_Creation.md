# SOP-002

# ADR / Result / Evidence Creation and Reference Management

Version: 1.0

Project:
H-Protein Space Crystal Intelligence

---

# Purpose

本SOPは、

- Project Charter
- Roadmap
- ADR
- Result
- Evidence
- Research Seed

において、

知見の出典を明確化し、

将来的な

- 論文化
- 研究費申請
- 知識継承
- AI学習用知識基盤構築

を容易にすることを目的とする。

---

# Basic Principle

Research OSで扱う知識は、

「LLMが理解する形式」

ではなく、

「研究者が10年後に見て理解できる形式」

で記録する。

可読性を最優先とし、

Author-Year形式を標準とする。

---

# Citation Rule

## Allowed

本文中では以下の形式を使用する。

例

H-protein結晶の構造は
0.88 Å分解能で決定された
(Higashiura et al., 2010)。

高圧凍結法によって
0.86 Å構造が得られた
(Higashiura et al., 2013)。

宇宙結晶では
0.79 Åデータ収集が達成された
(東浦・中川, 2012)。

---

## Not Allowed

以下のような形式は保存しない。

例

- 【1-ca8e9f】
- 【2-96fe02】
- turn11search1
- turn11search2
- ChatGPT内部参照
- Copilot内部参照

Research OSでは
人間可読な引用形式のみ使用する。

---

# Reference Categories

## Published

査読済み論文

例

- Higashiura et al., 2010
- Higashiura et al., 2013
- Hirano et al., 2016

---

## Review

総説

例

- 東浦・中川, 2017

---

## Submitted

投稿済み

例

- Higashiura et al., submitted

---

## In Preparation

執筆中

例

- Higashiura et al., in preparation

---

## Conference

学会発表

例

- Higashiura et al., ACA 2025

---

## Internal Report

プロジェクト文書

例

- H-Protein Project Internal Report, 2025

---

## Unpublished Observation

未発表データ

例

- Higashiura laboratory, unpublished observation

---

# Unpublished Data Rule

未発表データは必ず明示する。

例

宇宙結晶から
0.73 Åデータ収集に成功した
(Higashiura laboratory, unpublished observation)。

リン酸アンモニウム条件により
クラスター形成が大幅に抑制された
(Higashiura laboratory, unpublished observation)。

未発表データを
Publishedとして記載してはならない。

---

# ADR Rule

ADRは

「なぜその意思決定をしたか」

を記録する文書である。

### 必須項目

- Context
- Decision
- Alternatives
- Consequences
- References

---

# Result Rule

Resultは

「何を達成したか」

を記録する文書である。

### 推奨構造

- Background
- Objective
- Result
- Interpretation
- Limitation
- Next Action
- References

Resultには可能な限り定量値を記載する。

例

- 0.88 Å
- 0.86 Å
- 0.79 Å
- 0.73 Å
- 水素可視化率
- Completeness
- Multiplicity

---

# Evidence Rule

Evidenceは

「Resultを裏付ける事実」

を保存する文書である。

例

- 回折像
- 精密化統計
- Electron Density
- Hydrogen Count
- Cryo条件
- Dose条件

Evidenceには解釈を書きすぎない。

事実を優先する。

---

# Research Seed Rule

Research Seedは

未来の研究アイデアを保存する文書である。

例

- Information Content Score
- Chunk Analysis
- ODC
- GNN
- RL
- Charge Density Prediction

Seedは未検証でよい。

否定された場合でも削除しない。

状態を更新する。

例

- Seed
- Active
- Validated
- Rejected

---

# Project-Specific Rule

H-Protein Space Crystal Intelligenceでは

以下を重要概念として扱う。

## Crystal Quality

結晶品質

---

## Information Recovery

回折データから失われない情報量

---

## Hydrogen Visibility

超高分解能データ品質指標

---

## Information Content

構造解析から得られる科学的情報量

---

## Charge Density

最終的な到達目標の一つ

---

## Crystal Intelligence

知識化・予測・設計を行う統合概念

---

# Result Reference Section

Result文書には可能な限り

References節を設ける。

例

## References

Higashiura et al., 2010

Higashiura et al., 2013

東浦・中川, 2017

Higashiura laboratory, unpublished observation

---

# Principle

Create Crystal

↓

Acquire Information

↓

Extract Information

↓

Create Knowledge

Research OS上の全ての知識は、
この流れのどこに位置するかを意識して記録する。
