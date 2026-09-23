# Typed Decisions

## Core hypothesis

Jevを「小さいLLM」とだけ捉えず、agent runtimeにおけるbounded decision interfaceとして研究する。

## Comparison

### Free-form generation

モデル → 自然言語 → parser → control flow

### Typed decision

state → finite options / score / abstain → control flow

## Questions

- schemaをどこまで固定できるか
- abstentionをどう扱うか
- probability/calibrationをどう測るか
- decisionsをreplay可能なeventとして保存できるか
- typed layer自体が新しい失敗点にならないか
