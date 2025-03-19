# tidb-docs-reviewer
A GitHub Action that leverages OpenAI's GPT-4 API to provide intelligent feedback and suggestions on your pull requests.

## Features

- Automatically reviews pull requests when they are opened or updated
- Analyzes code changes and provides helpful suggestions
- Ignores files matching specified patterns
- Posts review comments directly on the PR

## Setup

### Prerequisites

- Node.js 16 or higher
- pnpm (recommended) or npm

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/tidb-docs-reviewer.git
cd tidb-docs-reviewer
```

2. Install dependencies:
```bash
pnpm install
```

3. Build the project:
```bash
pnpm build
```

## Usage

### Local Development

To run the project locally for development:

```bash
pnpm build
pnpm start
```

### GitHub Action Configuration

To use this as a GitHub Action, create a workflow file in your repository (e.g., `.github/workflows/docs-reviewer.yml`):

```yaml
name: TiDB Docs Reviewer

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: TiDB Docs Reviewer
        uses: yourusername/tidb-docs-reviewer@main
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
          OPENAI_API_MODEL: "gpt-4-1106-preview"
          exclude: "*.md,*.json,*.yml,*.yaml"
```

## Configuration Options

| Option | Description | Required | Default |
|--------|-------------|----------|---------|
| `GITHUB_TOKEN` | GitHub token for API access | Yes | N/A |
| `OPENAI_API_KEY` | OpenAI API key | Yes | N/A |
| `OPENAI_API_MODEL` | OpenAI model to use | No | "gpt-4-1106-preview" |
| `exclude` | Comma-separated list of glob patterns to exclude | No | "" |

## License

ISC
