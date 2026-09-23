# JEV SCOUTER

## Premise

宇宙人が地球人を調査するために使う「Jev Scouter」。

この装置は発言内容そのものではなく、発言から推定される意思決定を評価する。

特に日本人の曖昧な発話を測定すると、宇宙人の理解を超えた結果が出る。

## Basic example

人間:

> 「はい。」

JEV Scouter:

```
表層: YES
意図: UNKNOWN
拒否確率: 0.73
同意確率: 0.18
社交的応答: 0.91
本音の開示: 0.04
```

宇宙人:

> 「なぜYESと言っているのにYESではない？」

人間:

> 「いや、まあ……はい。」

宇宙人:

> 「さらにわからなくなった。」

## The misunderstanding

宇宙人は当初、日本人を「意思決定能力が低い種族」と評価する。

しかし調査を進めると、別の特徴が発見される。

日本人は発話前に相手の状態・関係・場の空気・将来の反応を推測している。

つまり、

- 直接性: 低い
- 明示性: 低い
- 自己主張: 低い
- 相手モデル: 高い
- 文脈利用: 高い
- 衝突回避: 高い
- 意味の圧縮: 高い

という別種の意思決定方式を持つ。

## The key idea

Jev Scouterは「本音を読む機械」ではない。

**次に必要な判断を推定する機械**である。

例えば、

> 「今日はちょっと……」

を、

```
decision = ASK_CLARIFICATION
confidence = 0.87

latent_options:
  - decline
  - fatigue
  - social_obligation
  - financial_constraint
```

のように分解する。

ところが日本人同士では、この一言だけで会話が成立する。

## The anomaly

ある日本人を測定すると、

```
YES       12%
NO         8%
ABSTAIN    3%
UNKNOWN   77%
```

という異常値になる。

宇宙人は装置の故障だと考える。

しかし故障ではない。

その人物は、人類自身がまだ決定していない未来について話していた。

Jev ScouterがUNKNOWNを返したのは、

**測定できなかったからではなく、まだ決まっていなかったから。**

## Science-fiction question

宇宙人は初めて考える。

> 「意思決定とは、存在する答えを選ぶことなのか。
> それとも、まだ存在しない答えを作ることなのか。」

## Research connection

research-jev の typed decision layer を、異文化理解・異種知性・SF的な観測装置へ拡張する。

関連するJevの判断:

1. Which files?
2. Which model?
3. Safe to run?
4. Done?
5. Keep or drop?
6. **Who decides?**

SF版ではさらに、

**「Is the decision already determined?」**

を測る。

これは、意思決定を分類する機械が、未来そのものを観測してしまうという逆説につながる。

Research fiction seed: 2026-09-24
