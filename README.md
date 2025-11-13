# ExplainThisError – GitHub Action

Post build/test errors to ExplainThisError and get a structured root cause + fixes.
Emits GitHub Annotations and a rich step summary.

## Inputs

- `api-url` (required): Base URL, e.g. `https://api.explainthiserror.com`
- `api-key` (required): CI key issued by ExplainThisError (Bearer token)
- `error` (required): Error text to analyze
- `file` (optional): Source file path related to the error
- `line` (optional): Line number
- `job`  (optional): Job name
- `step` (optional): Step name

## Example

```yaml
- name: Explain this error
  uses: explainthiserror/action@v1
  with:
    api-url: ${{ vars.ETE_API_URL }}
    api-key: ${{ secrets.ETE_CI_KEY }}
    error: ${{ steps.tests.outputs.last_error }}
    file:  "backend/app.py"
    line:  "278"
    job:   ${{ github.job }}
    step:  "pytest"
