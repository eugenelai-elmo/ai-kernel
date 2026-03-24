<!-- substrate/navigation.md -->
# Token-Efficient Code Navigation

## Rule: Read symbols, not files

Never read an entire file to find one thing. Use Serena symbol tools:
- `get_symbols_overview` — all symbols in a file (no bodies)
- `find_symbol` with `include_body=false` — locate the symbol
- `find_symbol` with `include_body=true` — read only when needed
- `find_referencing_symbols` — understand call chains

## Search order

1. Know the symbol name → `find_symbol`
2. Know the file, not the symbol → `get_symbols_overview`
3. Pattern/regex needed → `search_for_pattern`
4. Cross-file semantic → `find_referencing_symbols`
5. Last resort → `Read` the file

## Never

- `grep` the whole repo to find a class definition — use `find_symbol`
- Read 500 lines to find 10 relevant ones — use symbol tools
- Re-read a file you already read this session — use your context

## Token budget heuristic

Before reading a file, ask: can I get what I need from the symbol overview first?
If yes — do that. Reading is irreversible (it costs tokens you can't un-spend).
