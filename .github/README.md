# GitHub CI/CD Configuration

This directory contains all GitHub-specific configurations for the Cafe Ordering System project.

## 📁 Directory Structure

```
.github/
├── workflows/               # GitHub Actions workflows
│   ├── pr-validation.yml   # Validates PRs (lint, type-check, build)
│   └── pr-labeler.yml      # Auto-labels PRs based on changed files
├── CODEOWNERS              # Defines code review requirements
├── labeler.yml             # Configuration for auto-labeler
├── pull_request_template.md # Template for new PRs
└── README.md               # This file
```

## 🚀 Workflows

### 1. PR Validation (`pr-validation.yml`)

**Purpose:** Ensures code quality and prevents broken code from being merged.

**Runs on:** Every pull request to `master` branch

**Checks performed:**
- ✅ ESLint - Code quality and style
- ✅ TypeScript - Type checking
- ✅ Prisma - Schema validation
- ✅ Build - Next.js build verification

**Status:** Required check - PR cannot merge if this fails

### 2. PR Auto Labeler (`pr-labeler.yml`)

**Purpose:** Automatically categorizes PRs for better organization.

**Runs on:** Every pull request

**Actions:**
- Adds labels based on changed files (frontend, backend, database, etc.)
- Adds size labels (xs, s, m, l, xl) based on number of lines changed
- Helps reviewers quickly understand the scope of changes

## 👥 Code Owners

The `CODEOWNERS` file ensures critical code is reviewed by the right people.

**Current configuration:**
- **@mayankpawar24** - Required reviewer for all changes
- Specific ownership for:
  - Database schema (`/prisma/**`)
  - API routes (`/src/app/api/**`)
  - Configuration files
  - GitHub workflows

## 📝 Pull Request Template

The `pull_request_template.md` provides a standardized structure for all PRs, including:

- Description of changes
- Type of change checklist
- Testing checklist
- Screenshots section (for UI changes)
- Database changes section
- Reviewer checklist

## 🏷️ Auto Labels

The labeler automatically applies these labels:

| Label | Applied When |
|-------|-------------|
| 🎨 frontend | Component, page, or styling changes |
| ⚙️ backend | API routes or server-side logic |
| 🗄️ database | Prisma schema modifications |
| 📘 types | TypeScript type definitions |
| 📝 docs | Documentation updates |
| 🔧 config | Configuration file changes |
| 🚀 ci-cd | GitHub Actions or CI/CD changes |
| 👥 customer | Customer-facing features |
| 👤 admin | Admin panel features |
| 🛒 orders | Order management |
| 🍽️ menu | Menu management |
| ⚙️ settings | Settings features |

**Size labels:**
- `size/xs` - < 10 lines changed
- `size/s` - < 100 lines changed
- `size/m` - < 500 lines changed
- `size/l` - < 1000 lines changed
- `size/xl` - > 1000 lines changed

## 📖 Usage

### For Developers

1. **Create feature branch:**
   ```bash
   git checkout -b feature/your-feature
   ```

2. **Make changes and commit:**
   ```bash
   git add .
   git commit -m "feat: your changes"
   ```

3. **Before pushing, verify locally:**
   ```bash
   npm run validate  # Lint + type-check
   npm run build     # Verify build works
   ```

4. **Push and create PR:**
   ```bash
   git push origin feature/your-feature
   # Then create PR on GitHub
   ```

5. **Wait for automated checks and approval:**
   - GitHub Actions will run automatically
   - Fix any failures
   - Wait for @mayankpawar24 to review and approve

6. **Merge after approval:**
   - Only possible after approval + passing checks

### For Reviewers

1. **Review the PR description** - Check completeness
2. **Check auto-applied labels** - Understand scope
3. **Review automated checks** - All must be green
4. **Review code changes** - Quality and architecture
5. **Test locally if needed** - For critical changes
6. **Approve or request changes**

## 🔧 Maintenance

### Adding New Labels

Edit `.github/labeler.yml` to add new auto-labeling rules.

### Modifying Required Checks

1. Update workflow files in `.github/workflows/`
2. Update branch protection rules in GitHub Settings

### Changing Code Owners

Edit `.github/CODEOWNERS` to modify review requirements.

## ✅ Benefits

✨ **Automated Quality Checks** - Catch issues before merge
✨ **Standardized PRs** - Consistent format and information
✨ **Protected Master Branch** - No direct commits allowed
✨ **Clear Review Process** - Required approval from team leader
✨ **Better Organization** - Auto-labeled PRs for easy filtering
✨ **Improved Collaboration** - Clear workflow for all team members

## 📚 Documentation

For detailed setup instructions, see:
- [GITHUB_SETUP.md](../GITHUB_SETUP.md) - Complete setup guide
- [README.md](../README.md) - Main project documentation

## 🆘 Support

If workflows fail or you encounter issues:

1. Check workflow logs in GitHub Actions tab
2. Review [Troubleshooting](../GITHUB_SETUP.md#troubleshooting) section
3. Verify branch protection settings
4. Contact @mayankpawar24 for assistance
