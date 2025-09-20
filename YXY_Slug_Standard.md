# YXY_Slug 

**Goal**: For research test

- ## Core rules

  

  1. Uppercase all letters.(e.g., abc → ABC).
 
  2. Keep only [A–Z][0–9][-]. Remove everything else after normalization.

  3. Collapse multiple hyphens to one; trim leading/trailing hyphens.

  4. Treat spaces, tabs, underscores, slashes and plus signs as separators → each run becomes a single -.

  5. Stopwords (English): remove a,A, an,AN, the,THE, of,OF, and,AND when they appear as standalone tokens

     

  ## Examples

  - abc → ABC
  - Hello World世界您好` → HELLO-WORLD
  - Foo Bar\tBaz_ → FOO-BAR-BAZ
  - The Benefits of AI and ML → BENEFITS-AI-ML

  - path/to/file → PATH-TO-FILE
