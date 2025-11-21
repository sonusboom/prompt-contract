# PowerShell Guidelines (Prompt Contract Examples)

Examples showing how PowerShell should look under the Prompt Contract.

---

## Function Naming & Structure
- Use PascalCase  
- Use approved verbs  
- Functions return structured objects, not raw strings  

**Example:**
```powershell
function Get-Config {
    param(
        [string]$Path
    )

    return (Get-Content -Path $Path | ConvertFrom-Json)
}
```

---

## Clear Parameter Block
Every script requires a top-level `param()` block.

```powershell
param(
    [string]$InputPath,
    [switch]$Verbose
)
```