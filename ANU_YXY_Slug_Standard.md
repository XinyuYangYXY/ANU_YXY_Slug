# ANU_YXY_Slug 

**Goal**: Deterministic, URL-friendly slugs.

## Core rules
1. Lowercase all letters.
2. Unicode normalize (NFKD) and **strip diacritics** (e.g., “Café” → “Cafe”).
3. **CamelCase split**: insert hyphen at lower→Upper or letter→digit boundaries (e.g., makeHTTPRequest → make-http-request).
4. Treat spaces, tabs, underscores, slashes and plus signs as **separators** → each run becomes a single `-`.
5. Replace any **sequence of non-alphanumeric** ASCII characters with a single `-`.
6. Keep only `[a–z 0–9 -]`. Remove everything else after normalization.
7. Collapse multiple hyphens to one; **trim** leading/trailing hyphens.
8. **Version tokens**: turn digit-dot-digit into hyphen (e.g., `v2.0` → `v2-0`).
9. **Stopwords** (English): remove `a, an, the, of, and` when they appear as **standalone tokens** (after tokenization), then re-collapse hyphens.
10. **Empty result →** `n-a`.
11. **Max length = 60** chars. Prefer cutting at the last hyphen ≤ 60; if none, hard cut at 60. Trim hyphens again.

## Examples (speculative outputs)
- `Hello World世界您好` → `hello-world`
- `A__B---C!!!` → `a-b-c`
- `  Foo  Bar\tBaz_ ` → `foo-bar-baz`
- `  __  ` → `n-a`
- `Café crème` → `cafe-creme`
- `Read_me v2.0` → `read-me-v2-0`
- `makeHTTPRequest` → `make-http-request`
- `The Benefits of AI and ML` → `benefits-of-ai-ml`
- `path/to/file` → `path-to-file`

## Java hints
- Use `java.text.Normalizer` (NFKD) + regex to strip `\p{M}` combining marks.
- CamelCase split regex example: `s.replaceAll("([a-z0-9])([A-Z])", "$1-$2")`.