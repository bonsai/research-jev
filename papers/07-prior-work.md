# 先行研究マップ

このファイルは、Jev / typed-decision runtime の仮説に直接関係する先行研究を、**意思決定の型**ごとに整理する。

## 1. Agent architecture / runtime

LLM agent は、LLM 単体ではなく、memory・planning・tool use・実行ループを含むシステムとして研究されている。2026年のサーベイでも、architecture / control flow / reliability / evaluation / scalability が主要論点として整理されている。

**Jevへの接続**
- 「モデルを賢くする」だけでなく、loop の外側に decision policy を置く研究空間がある。
- Jev の5判断は、この runtime 層をさらに typed decision layer として切り出す仮説と読める。

Reference:
- A Survey on LLM Agents: Architecture, Applications, and Challenges (IEEE/ICOIN 2026)
- From Language Models to Agentic AI (Cognitive Computation, 2026)

## 2. Tool selection / routing

2025–2026年の研究では、tool selection は単なる function calling ではなく、retrieval、ranking、authorization、execution、memory、human-in-the-loop を含む production architecture の問題として整理されている。

特に Tool and Agent Selection for LLM Agents in Production は、手動選択、UI、retrieval-based selection、autonomous selection を統合した taxonomy を提示している。

**Jevへの接続**
- 「Which tool?」を Jev の第6判断候補として追加できる。
- 「Which files?」と「Which tool?」は、どちらも候補集合からの bounded selection として同じ型にできる可能性がある。

Reference:
- Lumer et al., Tool and Agent Selection for Large Language Model Agents in Production, 2025/2026

## 3. Model routing / cascading

LLM routing では、query ごとにモデルを選ぶ routing と、必要に応じて強いモデルへ昇格する cascading が研究されている。

Dekoninck et al. (ICML 2025) は routing と cascading を統一的に扱い、cost-performance trade-off の条件を分析している。

**Jevへの接続**
- 「Which model?」は frontier model 内部の reasoning ではなく runtime policy として扱える。
- routing decision の入力を task state / difficulty / cache / phase などの typed state に限定できる。

Reference:
- Dekoninck, Baader, Vechev, A Unified Approach to Routing and Cascading for LLMs, ICML 2025

## 4. Context engineering / compression

長い tool-use trajectory では、全履歴を保持すること自体がコスト・性能上の問題になる。

2026年の研究では、tool interaction の選択的保持と要約を比較し、全履歴より少ない context で高い completion を得られるケースが報告されている。また ACL 2026 の研究では、long-horizon agent training において summarization-based context management を組み込み、固定 context window を超える tool-use を扱っている。

**Jevへの接続**
- 「Which files?」= context inclusion
- 「Keep or drop?」= retention / compression
- context policy を generation から分離し、typed state transition として記録できる。

References:
- Lodha et al., Less Context, Better Agents, 2026
- Lu et al., Beyond the Context Window, ACL 2026

## 5. Runtime safety / tool gating

2026年の研究では、agent safety をモデルの性質だけでなく runtime の enforceable policy として扱う方向が強まっている。

Doshi et al. は STPA による hazard analysis と、capability / confidentiality / trust level を構造化した MCP framework を提案している。これは tool sequence と data flow に対して安全要件を明示的に適用する考え方である。

**Jevへの接続**
- 「Safe to run?」は generation の一部ではなく runtime contract にできる。
- typed capability、permission、trust、irreversibility を decision input にする設計が考えられる。
- deny / allow / human-review の3値以上を持つことも重要。

Reference:
- Doshi et al., Towards Verifiably Safe Tool Use for LLM Agents, ICSE 2026

## 6. Termination / evidence

「Done?」は独立した研究対象になりつつある。

2026年の Evidence-Carrying Termination は、agent が COMPLETE を返す際に、要求された主張を execution trace の証拠へ結びつける typed certificate と deterministic replay を要求する設計を検討している。

**Jevへの接続**
- termination を free-form self-evaluation から typed evidence check に移せる。
- test result、diff、command result、required artifact を termination input にできる。
- 「done / continue / recover / ask-human」のような有限状態として扱える。

Reference:
- Liu, When May an Agent Stop? Evidence-Carrying Termination for Tool-Using LLMs, 2026

## 7. Typed decision layer という研究上の位置

ここまでの先行研究を並べると、既存研究はそれぞれ

- tool selection
- model routing
- context management
- safety gating
- termination verification

を個別問題として扱う傾向がある。

**research-jev の仮説は、それらを共通の「typed decision layer」として runtime 上に統合して観察すること。**

つまり新規性候補は「小さいモデル」そのものではなく、

> bounded decision を typed state → finite action / score / abstain → runtime transition に変換する設計

に置く。

## 8. 既存研究との差分を検証する問い

1. 5つの decision は本当に独立しているか。
2. Which files? と Which tool? は同じ selector abstraction に統合できるか。
3. Which model? は routing / cascading とどこまで同型か。
4. Safe to run? は policy engine / capability system とどこが違うか。
5. Done? は verifier / evidence certificate とどこまで重なるか。
6. Keep or drop? は context compression / memory management と同一問題か。
7. typed decision にすることで calibration / abstention / replayability は改善するか。
8. decision layer 自体の誤りが新しい failure mode を生まないか。
9. decision cost を frontier generation cost と分離して測れるか。
10. 5判断を一つの runtime schema に統合することに、本当に追加価値があるか。

## Evidence policy

数値・改善率・安全性の主張は原論文の条件と実験設定を併記する。production benchmark、synthetic benchmark、community report、own measurement を混同しない。

Research update: 2026-09-24
