# Python Guidelines (Prompt Contract Examples)

These examples illustrate how the Prompt Contract enforces consistent, human-quality Python output.

---

## Function & Variable Naming

- Use `snake_case` for variables and functions  
- Use `UpperCamelCase` for classes  
- Avoid AI-style long names  
- Keep functions focused and short

**Example:**
```python
def load_config(path: str) -> dict:
    with open(path, 'r', encoding='utf-8') as fh:
        return json.load(fh)
```

---

## CLI Structure
Every CLI Python script must use `argparse` and include a `main()` entrypoint.

**Example:**
```python
import argparse

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("--path", required=True)
    args = parser.parse_args()

    print(f"Loading: {args.path}")

if __name__ == "__main__":
    main()
```