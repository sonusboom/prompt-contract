# Prompt Contract (v5)

This project came out of my own struggle to communicate clearly and consistently with ChatGPT while learning to code in Python. 
I’m still very early in my python journey — but I care deeply about writing clean, senior-developer-level code. ChatGPT has been a *massive* force multiplier for me, yet I kept running into the same problems: inconsistent output, unnecessary explanations, hallucinated details, and scripts that felt more “AI-generated” than “human-written.”

So I built this **Master Prompt Contract** — a structured, enforceable set of instructions that transforms ChatGPT into a predictable, concise, senior-developer-styled coding assistant.

---

## 🌱 Why I Created This

As a learner, I often knew *what* I wanted but not the “right” way to ask for it.  
I’d get:

- overly verbose explanations  
- code that tried to teach instead of solve  
- inconsistent naming conventions  
- scripts with unnecessary complexity  
- hallucinated APIs and paths  
- half-complete patches  
- or walls of text when I just wanted a function

At the same time, I was pushing myself to improve — I wanted the code I wrote (or had ChatGPT generate) to be more human-like and something a senior developer would be comfortable reviewing.

But without clear boundaries, ChatGPT was… unreliable.

This contract fixed that.

---

## 🔧 What This Contract Does for Me

**Prompt Contract v5** enforces the exact behavior I always wished ChatGPT would follow:

- concise, clean outputs  
- Python code with `argparse` and proper `main()` structure  
- Bash scripts with short variable names and `set -euo pipefail`  
- PowerShell functions using approved verbs and typed parameters  
- zero hallucination  
- zero over-engineering  
- no teaching mode  
- no fluff  
- direct, senior-dev style tone  
- full, copy/paste-ready rewrites instead of fragments  

And importantly:

### ✔ Minimal clarifications  
ChatGPT only asks questions *when it truly needs to*.

### ✔ Reasonable defaults  
If something is standard practice, ChatGPT just proceeds.

This keeps the flow fast and productive.

---

## 🚀 How It Helps Me Learn

Instead of wading through noisy explanations or fixing oddly structured code, I now see:

- clean architecture  
- consistent formatting  
- realistic naming conventions  
- practical patterns  
- maintainable scripts  
- and no “AI slop”

---

## 📄 What’s Included

The examples show what the code structure should resemble upon contract enforcement

```
master_prompt_contract_v5.md   # Full Contract
examples/
  ├── python_guidelines.md
  ├── bash_guidelines.md
  └── powershell_guidelines.md
README.md                      # You are here
```

---

## 🧩 How to Use It

1. Open a new ChatGPT session.  
2. Paste in the entire contents of `master_prompt_contract_v5.md`.  
3. (Optional) Upload the file directly — ChatGPT will treat it as the authoritative baseline.  
4. Start coding. Enjoy deterministic, clean, senior-dev-style output.

---

## License

MIT License  
See the LICENSE file in this repository for full text.

---

## Contributions

Pull requests and refinements are welcome — especially from those building tools, scripts, or frameworks around LLM reliability.