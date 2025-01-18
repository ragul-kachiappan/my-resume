# my-resume

Resume built using [JSON Resume](https://jsonresume.org/), a JSON-based standard for creating and sharing resumes.

- [My Resume](https://registry.jsonresume.org/ragul-kachiappan)
- [Associated Gist](https://gist.github.com/ragul-kachiappan/da348834c0cc28fa912cf480f1f3a610)

## TODO
- Add resumed dependency instructions

## Setup Requirements

- [direnv](https://direnv.net/) - For automatic environment loading
- [uv](https://github.com/astral-sh/uv) - Fast Python package installer
- Python virtual environment
- [pre-commit](https://pre-commit.com/) - Git hooks manager

## Initial Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/my-resume.git
cd my-resume
```

2. UV sync environment
```bash
uv sync
```
3. Set up Python virtual environment:
```bash
python -m venv .venv
```

4. Create `.envrc` for direnv:
```bash
echo "source .venv/bin/activate" > .envrc
```

5. Allow direnv:
```bash
direnv allow
```

6. Install dependencies using uv:
```bash
uv pip install pre-commit
```

7. Set up pre-commit:
```bash
pre-commit install
```

## Pre-commit Usage

The repository includes pre-commit hooks for JSON validation and formatting. These hooks run automatically on every commit, but you can also run them manually:

- Run on all files:
```bash
pre-commit run --all-files
```

- Run on staged files:
```bash
pre-commit run
```

- Update pre-commit hooks to latest versions:
```bash
pre-commit autoupdate
```

## JSON Resume

Edit your resume by modifying the `resume.json` file following the [JSON Resume Schema](https://jsonresume.org/schema/).

NOTE: You will have to take care of hosting. I created a gist with their [editor](https://registry.jsonresume.org/editor) and then created this repo to maintain and update my resume. Refer to the Getting Started guide in [JSON Resume](https://jsonresume.org/getting-started)

## Development Workflow

1. Activate the environment (automatic with direnv):
```bash
# If not using direnv:
source .venv/bin/activate
```

2. Make changes to your resume.json
3. Commit changes - pre-commit will automatically validate and format your JSON files
4. Push to repository

## Notes

- The pre-commit hooks will ensure your JSON files are properly formatted and valid
- direnv will automatically activate your Python environment when you enter the directory
- uv provides faster package installation compared to traditional pip


## GitHub Actions - Auto-Update Resume Gist

This repository includes a GitHub Action that automatically updates a GitHub Gist containing your resume whenever changes are pushed to `resume.json` in the main branch.

### Setup Instructions

1. Create a GitHub Personal Access Token:
   - Go to [GitHub Settings > Developer Settings > Personal Access Tokens](https://github.com/settings/tokens)
   - Generate a new token with the `gist` scope
   - Copy the token value

2. Add the token to your repository secrets:
   - Go to your repository Settings > Secrets and Variables > Actions
   - Click "New repository secret"
   - Name: `TOKEN`
   - Value: Paste your personal access token

3. Create a GitHub Gist:
   - Go to [gist.github.com](https://gist.github.com)
   - Create a new gist with your resume.json
   - Copy the gist ID from the URL (it's the string after the last slash)

4. The workflow is already configured in `.github/workflows/update-gist.yml`. It will:
   - Trigger when changes are pushed to `resume.json` in the main branch
   - Update your specified gist with the new content

Note: The gist ID in the workflow file should match your gist's ID. The current configuration uses ID: `da348834c0cc28fa912cf480f1f3a610`

## Rights and Usage

This repository is made public for reference and educational purposes. It demonstrates:
- JSON Resume implementation
- GitHub Actions automation
- Pre-commit hook configuration
- Development environment setup with direnv and uv

However, all rights are reserved. While you can use this repository as a reference to learn from and understand the implementation:
- The code, configurations, and content cannot be copied directly
- You should write your own implementation based on your understanding
- No part of this repository may be used, modified, or distributed without explicit permission

Feel free to:
- Study the code structure and patterns
- Learn from the GitHub Actions setup
- Understand how the various tools are integrated
- Use these learnings to create your own implementation

P.S. This README was created in collaboration with Claude (Anthropic's AI assistant), through an iterative process of brainstorming and refinement.