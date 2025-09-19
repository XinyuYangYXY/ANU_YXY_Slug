# ANU_YXY_Slug 

**Goal**: For research test.

## Core rules
1. Uppercase all letters.(e.g., abc → ABC).
2. CamelCase split: insert hyphen at lower→Upper or letter→digit boundaries (e.g., makeHTTPrequest → make-http-request).
3. Collapse multiple hyphens to one; trim leading/trailing hyphens.
4. Treat spaces, tabs, underscores, slashes and plus signs as separators → each run becomes a single -.
5. Keep only [A–Z 0–9 -]. Remove everything else after normalization.
6. Version tokens: turn digit-dot-digit into hyphen (e.g., v2.0 → v2-0).
7. Stopwords (English): remove a,A, an,AN, the,THE, of,OF, and,AND when they appear as standalone tokens 
8. Empty result → N-A.
    
## Examples (speculative outputs)
- abc → ABC
- Hello World世界您好` → HELLO-WORLD
- a__b---c!!! → A-B-C
-   Foo  Bar\tBaz_  → FOO-BAR-BAZ
-      → N-A
- Read_me v2.0 → READ-ME-V2-0
- makeHTTPrequest → MAKE-HTTP-REQUEST
- The Benefits of AI and ML → BENEFITS-AI-ML
- path/to/file → PATH-TO-FILE

## Java hints
- Use java.text.Normalizer (NFKD) + regex to strip \p{M} combining marks.

- CamelCase split regex example: s.replaceAll("([a-z0-9])([A-Z])", "$1-$2").




