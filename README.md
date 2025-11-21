![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![LLM Contract](https://img.shields.io/badge/Prompt%20Contract-Strict-orange.svg)
![Status](https://img.shields.io/badge/Maintained-yes-blue.svg)

# Prompt Contract

This project came out of my own struggle to communicate clearly and consistently with ChatGPT while learning to code in Python. 
I’m still very new in my python journey and I want to architect clean, senior-developer-like code. ChatGPT has been a force multiplier for me on this journey, yet I kept running into the same problems: inconsistent output, unnecessary explanations, hallucinated details, and scripts that felt more “AI-generated” slop than “human-written.”

So I put together this **Prompt Contract** as a structured, enforceable set of instructions that transforms ChatGPT into a predictable, concise, senior-developer-styled coding assistant.

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

This contract has greatly improved that.

---

## 🔧 What This Contract Does for Me

**Prompt Contract** enforces the exact behavior I always wished ChatGPT would follow by default:

- concise, clean outputs  
- Python code with `argparse` and proper `main()` structure  
- Bash scripts with short variable names and `set -euo pipefail`  
- PowerShell functions using approved verbs and typed parameters  
- low hallucination  
- low over-engineering  
- no teaching mode  
- no fluff  
- direct, senior-dev style and tone

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
3. (Optional) Upload the file directly.
4. Confirm that ChatGPT or LLM of choice understands the contract and will enforce it.

---

## License

MIT License  
See the LICENSE file in this repository for full text.

---

## Contributions

Pull requests and refinements are welcome — especially from those building tools, scripts, or frameworks around LLM reliability.

**Keywords:** prompt engineering, llm prompt contract, ai coding standards, chatgpt ruleset, hallucination control, developer tools, ai code generation, llm specification, prompt rules, llm behavior contract.