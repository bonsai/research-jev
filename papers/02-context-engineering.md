# Context Engineering

## Jev axis

Which files? / Keep or drop?

## Related directions

- dynamic context discovery
- selective tool/schema loading
- retrieval and reranking
- context compression
- externalized tool output

## Key hypothesis

必要なcontextを毎回frontier modelへ投入するのではなく、runtime側で選択・圧縮・再取得する。

## Evaluation

- input tokens
- retrieval precision
- task success
- latency
- recovery from omitted context
