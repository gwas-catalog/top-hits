# GWAS Association Tools

A command-line tool for genomic-wide association studies (GWAS) data validation and analysis.

## Features

- Validate:
  - Input: File path of GWAS Submission template that contains top associations
  - Output: Validation report of top associations

## Installation

Install from [PyPI](https://pypi.org/project/gwas-assoc-tools/):

```bash
pip install gwas-assoc-tools
```

## Usage

```bash
# Basic validation command
gwas-assoc validate <template excel file path>

# For help
gwas-assoc --help
gwas-assoc validate --help
```

## Development

### Setup

```bash
# Install uv (if not already installed)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install dependencies
uv sync --all-groups

# Activate virtual environment
source .venv/bin/activate
```

### Building and Installation

```bash
# Build the package (creates .whl and .tar.gz in dist/)
uv build

# Install your new package in development mode
uv sync --all-groups
```

### Release

Publishing is done by creating a GitHub Release. The release workflow builds the
package with `uv` and publishes to PyPI using trusted publishing, so no local
PyPI credentials or GitHub secrets are needed.

Before the first release, configure the PyPI project `gwas-assoc-tools` with a
GitHub trusted publisher:

- Owner: `EBISPOT`
- Repository: `gwas-assoc-tools`
- Workflow: `publish.yml`
- Environment: `pypi`

Configure the matching GitHub environment `pypi`; add reviewer protection if the
maintainers want manual approval.

### Testing

TODO

### Running with Real Files

```bash
# Run the CLI command through uv
# For failed test file
uv run gwas-assoc validate ./tests/test_fail.xlsx
# For successful test file
uv run gwas-assoc validate ./tests/test_success.xlsx


# Or after activating the shell
source .venv/bin/activate
# For failed test file
gwas-assoc validate ./tests/test_fail.xlsx
# For successful test file
gwas-assoc validate ./tests/test_success.xlsx

```

### Dependency Management

```bash
# Add a new dependency
uv add new-package

# Add a development dependency
uv add --group dev pytest-mock

# Check for dependency updates
uv lock --dry-run --upgrade

# Update dependencies
uv lock --upgrade
```

### Code Quality

```bash
# Run formatting
uv run black .
uv run isort .

# Run linting
uv run ruff check .

# Run type checking
uv run mypy src

# Run all formatting checks
uv run pre-commit run --all-files
```

## Documentation
Please find the Confluence page here: https://embl.atlassian.net/wiki/spaces/GOCI/pages/57606184/GWAS+Associations+Tools

## License

[License](LICENSE)
