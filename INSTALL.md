# Installation

## Codex

Copy the folders inside `skills/` into your Codex skills directory.

Windows PowerShell:

```powershell
$target = "$env:CODEX_HOME\skills"
Copy-Item -Recurse -Force .\skills\algo-learn-coach $target
Copy-Item -Recurse -Force .\skills\engineering-thinking $target
Copy-Item -Recurse -Force .\skills\ai-product-engineer $target
```

macOS/Linux:

```bash
cp -R skills/algo-learn-coach "$CODEX_HOME/skills/"
cp -R skills/engineering-thinking "$CODEX_HOME/skills/"
cp -R skills/ai-product-engineer "$CODEX_HOME/skills/"
```

Restart Codex or start a new task so the skills are discovered.

## Test Prompts

```text
Use algo-learn-coach to teach me two sum from a real problem, one line at a time.
```

```text
Use engineering-thinking to design a SaaS billing module.
```

```text
Use ai-product-engineer to design a RAG assistant for private company documents.
```

```text
Use ai-product-engineer first, then engineering-thinking, to plan an AI resume review product.
```
