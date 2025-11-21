# Prompt Contract

A concise, developer-grade framework for controlling LLM behavior and ensuring consistent, human-quality code generation.  
This repository contains the **Master Prompt Contract v5**, designed to eliminate hallucinations, enforce strict formatting, and produce predictable outputs across Python, Bash, and PowerShell.

---

## Overview

The **Prompt Contract** is a structured, enforceable specification that overrides default LLM behavior.  
It defines:

- Output standards  
- Code style rules  
- Hallucination controls  
- Formatting requirements  
- Behavior constraints  
- Patch/rewrites expectations  

It ensures AI-generated scripts are production-ready, minimal, and human-like.

---

## Why This Exists

Modern LLMs are powerful but inconsistent. Developers often struggle with:

- AI verbosity  
- Over-engineered “enterprise” scaffolding  
- Hallucinated APIs & functions  
- Formatting drift  
- Unpredictable naming conventions  

This contract fixes those problems by giving the model a **binding operating framework**.

---

## Repository Contents

```
master_prompt_contract_v5.md   # Full Contract
examples/
  ├── python_guidelines.md
  ├── bash_guidelines.md
  └── powershell_guidelines.md
README.md                      # You are here
```

---

## How to Use the Contract

1. Include the contract in your prompt (or reference it in a system prompt).
2. Tell the model: “Follow the Prompt Contract.”
3. Provide your task (script, patch, rewrite, etc.).
4. The model outputs code/conduct that adheres to the contract.

This works for:
- Code generation  
- Refactoring  
- Security scripting  
- Documentation  
- Multi-language toolchains  

---

## Examples

See the `/examples` directory for clear, minimal examples of what compliant output looks like in:

- Python  
- Bash  
- PowerShell  

These examples help onboard teammates and ensure consistent use.

---

## SEO Keywords (for discoverability)

LLM, prompt engineering, prompt contract, AI coding standards, hallucination control, ChatGPT ruleset, AI output specification, developer prompt framework.

---

## Full Contract

You can read the full **Master Prompt Contract v5** here:

`master_prompt_contract_v5.md`

---

## License

MIT License (or your preference).  
Add your license file to the repository root.

---

## Contributions

Pull requests and refinements are welcome — especially from those building tools, scripts, or frameworks around LLM reliability.