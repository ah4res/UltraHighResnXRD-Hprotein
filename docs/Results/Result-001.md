# Result-001
## ADR-001派生解析：超高分解能結晶学データにおけるチャンク再構成・結晶選別・多結晶マージの評価

### 背景

ADR-001では、超高分解能H-proteinデータセットを対象に、

1. chunk化による情報回復
2. pairwise CCによる結晶選別
3. multi-crystal mergeによる高分解能化

が可能かを検証した。

当初仮説は、

「低品質chunkの除去」
または
「類似結晶のみの選別」

によって、従来のfull data processingを上回る超高分解能データを構築できる、であった。

---

## Phase 1：chunk化・再構成評価

### 実施内容

各結晶のfull dataを

- 5°
- 10°
- 20°

chunkへ分割した。

さらに

- independent indexing
- reference-based indexing

を行い、

AIMLESSにより再マージした。

---

### 結果

5° chunkの推奨分解能とfull data推奨分解能の相関はほぼ消失していた。

r ≈ 0.04

であり、

高分解能に見えるchunkは必ずしも高品質結晶に由来しなかった。

5° chunkで観測される高分解能推奨値は、

不完全くさびに起因する統計的アーティファクトと考えられた。

また、

- 5° reference AIMLESS
- 20° reference AIMLESS

についても、

full dataを有意に上回る結果は得られなかった。

20° reference AIMLESSでは一時的に改善して見えたが、

連続CC1/2 cutoffで再評価すると

full median dmin = 0.892 Å

20° ref median dmin = 0.877 Å

となり、

Wilcoxon検定でも有意差は認められなかった。

---

### 考察

chunk化は中分解能データ処理では有効との報告が多い。

しかし本研究対象のような超高分解能データでは、

部分データ化に伴う

- completeness低下
- partiality増大
- high-resolution shellの不安定化

の影響が支配的となる。

したがって、

超高分解能領域においては

「full data > chunk data」

が基本である可能性が高い。

---

## Phase 2：pairwise CCによる結晶選別

### 実施内容

36結晶full datasetについて

IMEANからpairwise Pearson CCを計算した。

評価レンジ：

- full
- 4.0–1.5 Å
- 1.5–0.9 Å
- 1.0–0.9 Å

クラスタリング：

distance = 1 − CC

average linkage

---

### 結果

全体CCは非常に高かった。

最小CC

0.956

中央値CC

0.986

明瞭な異形結晶群は存在しなかった。

一方で、

glycerol濃度

- G00
- G05
- G10
- G15
- G20

に対応した弱いクラスタリング傾向は観察された。

しかし、

pairwise CC閾値による選別を行っても

全結晶マージを上回る結果は得られなかった。

---

### 考察

pairwise CCは

「結晶間類似性」

を検出できる。

しかし、

「超高分解能シグナルを持つかどうか」

を直接評価しているわけではない。

本データでは

結晶間差よりも

multiplicity増加の利益

の方が大きかった。

結果として、

似た結晶を選ぶより、

全結晶をマージする方が有利であった。

---

## Phase 3：multi-crystal merge

### 実施内容

以下の複数条件でAIMLESSマージを行った。

- pairwise CC選抜群
- G00+G05群
- G15+G20群
- 全結晶群

---

### 結果

n増加に伴い

- multiplicity上昇
- completeness向上
- dmin改善

が認められた。

代表例：

n=2
dmin ≈ 0.88 Å

↓

n=36
dmin ≈ 0.81 Å

n≧15以降では

0.81 Å付近で頭打ちとなった。

pairwise CC選抜群は

全結晶群を上回らなかった。

---

### 考察

本系においては

結晶選別の利益

＜

multiplicity増加の利益

と考えられる。

現段階では

「同型結晶は全部混ぜる」

という戦略がもっとも支持された。

---

## Phase 4：glycerol濃度の影響

### 背景

G00〜G10ではice-ringが観察された。

G15〜G20ではice-ringが減少した。

当初は

高glycerol群が優位

と予想された。

---

### 結果

pairwise CCでは濃度依存性が観察された。

しかし、

- dmin
- outer-shell CC1/2
- I/sigma

において

高glycerol群の明確な優位性は確認できなかった。

---

### 考察

現状のデータからは

「ice-ringが存在するとデータ品質が低下する」

という直接的根拠は得られていない。

可能性として、

1.
ice-ringは存在するが、
超高分解能データでは反射数が非常に多く、
統計量に埋もれてしまう

2.
glycerol濃度の違いは
結晶パッキングを大きく変化させていない

が考えられる。

少なくとも、

G00〜G20は依然として高い同型性を維持していた。

---

## Phase 5：結晶方位の評価

### 実施内容

GXPARM.XDSから

- orientation matrix
- reciprocal lattice orientation

を取得し、

- beam
- spindle axis

との角度を評価した。

---

### 結果

オペレータは方位を意識してマウントしていない。

しかし実際の結晶方位は完全ランダムではなかった。

例：

∠(b, beam)

中央値 73°

ランダム期待値 60°

KS p=0.0007

一方、

- dmin
- outer-shell CC1/2

と方位の相関は認められなかった。

G15+G20の差も方位では説明できなかった。

---

### 考察

結晶方位にはマウント由来の偏りが存在する。

しかし、

高分解能到達能を支配する因子とは考えにくい。

したがって、

今回観測された結晶間差は

方位効果では説明できない。

---

## Phase 6：検出器ジオメトリ限界

### 幾何条件

波長

0.70 Å

Detector distance

133 mm

Detector edge

0.83 Å

Detector corner

0.71 Å

---

### 結果

AIMLESS推奨分解能は

0.81 Å

付近で頭打ちとなった。

しかし、

0.83–0.71 Å領域にも

- CC1/2
- I/sigma
- Nmeas

は残存していた。

また異方性評価では

d1 = 0.79 Å
d2 = 0.84 Å
d3 = 0.89 Å

であった。

---

### 考察

0.81 Åは

結晶限界

というよりも

測定ジオメトリ限界

の可能性が高い。

評価空間が狭すぎるため、

選別アルゴリズムの真価を判断できていない可能性がある。

---

## Radiation Damage仮説

chunk、
pairwise CC、
glycerol、
orientation

の影響が限定的であったため、

残された主要な系統誤差として

Radiation Damage

が浮上した。

特に、

全結晶が異なる方位を持つため、

前半フレームのみを利用したmulti-crystal mergeによって

- multiplicity維持
- radiation damage低減

を両立できる可能性がある。

ただし、

その評価は

CC1/2やI/sigmaではなく、

- 電子密度
- 水分子数
- alternate conformation
- difference Fourier map

等による検証が必要である。

---

# 現時点での結論

### 支持された仮説

- 多結晶マージは有効
- multiplicity増加が主要因
- 0.83 Å以遠にも信号が存在する可能性
- 現在の測定系では分解能評価が飽和している

### 棄却または支持されなかった仮説

- chunk再構成による超高分解能回復
- pairwise CC選別による有意な改善
- glycerol濃度による大きな品質差
- 結晶方位による高分解能支配

### 次段階

High-energy settingの超高分解能データセットを用いて、

- pairwise CC選別
- high-resolution quality ranking
- radiation damage除去
- multi-crystal merge

を再評価する。

本研究は、

「何が有効か」

よりも、

超高分解能結晶学において

「何が有効でないか」

を体系的に示した点に意義がある。
