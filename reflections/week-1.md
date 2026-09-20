# Reflection — Week 1

## Q1. The concept, in my words

The model is a vendor I cannot see into. It will time out, rate-limit me, answer differently twice, and change its pricing while I sleep. So I put it behind one interface, validate everything it returns, and never let it be the only copy of an answer I already paid for.

## Q1b. Reading questions

1. `retryable` on `ModelError`: the only thing a caller may branch on.
2. `get_model_client()` reads `MODEL_PROVIDER`; `FallbackClient` hands the same request to a different provider, whereas `retry.py` tries the same provider again.
3. So CI needs no key, no network and no money, and can script a 429 on demand.

## Q2. What surprised me

That retrying a 400 is worse than not retrying a 500: it costs money and hides my own bug.

## Q3. What I would change

Return `truncated: true` when the document was cut to the context budget; today the caller cannot tell.

## Evidence

### Provider A

```
(dry run: no real key on the build machine)
```

### Provider B

```
(dry run)
```
