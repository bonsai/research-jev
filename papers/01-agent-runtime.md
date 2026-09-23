# Agent Runtime / Coding-Agent Loop

## Research question

Coding agentを「LLM単体」ではなく、観測・判断・tool execution・検証・terminationを反復するruntimeとして捉える。

## Jev connection

Jevの中心的な仮説は、loop内のbounded decisionsを明示的なtyped decision layerへ切り出せるか、という点にある。

## Evidence to collect

- loop architecture
- tool-call frequency
- termination criteria
- context growth
- cost per completed task

## Open question

どの判断を小型モデル・規則・確率モデルへ移しても品質を維持できるか。
