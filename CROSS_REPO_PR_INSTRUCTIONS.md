# Cross-Repo Pull Request Instructions

## How to Create a PR from this Fork to ethereum/EIPs

This document provides complete instructions for creating a pull request from branch `eip-draft-univ8-eth-initial` in `leeli01284-collab/EIPs` to the `ethereum/EIPs` repository.

### Required Information

- **Source Repository**: leeli01284-collab/EIPs
- **Source Branch**: eip-draft-univ8-eth-initial
- **Target Repository**: ethereum/EIPs
- **Target Branch**: main
- **PR Title**: `EIP draft: univ8.eth (initial minimal draft)`
- **Author**: leeli01284-collab (0x4b064115af4a16192cbbf0e0111a2417d0cf494b)
- **Fork PR Reference**: https://github.com/leeli01284-collab/EIPs/pull/4

### Step 1: Push the Branch

First, ensure the branch is pushed to your fork:

```bash
git push -u origin eip-draft-univ8-eth-initial
```

### Step 2: Create the Pull Request

#### Option A: Using GitHub Web UI

1. Go to https://github.com/ethereum/EIPs
2. Click on the **"Pull requests"** tab
3. Click **"New pull request"**
4. Click **"compare across forks"** (link near the top)
5. Set the following:
   - Base repository: `ethereum/EIPs`
   - Base branch: `main`
   - Head repository: `leeli01284-collab/EIPs`
   - Compare branch: `eip-draft-univ8-eth-initial`
6. Click **"Create pull request"**
7. Fill in the PR details (see below)
8. Click **"Create pull request"**

#### Option B: Using GitHub CLI

```bash
gh pr create \
  --repo ethereum/EIPs \
  --base main \
  --head leeli01284-collab:eip-draft-univ8-eth-initial \
  --title "EIP draft: univ8.eth (initial minimal draft)" \
  --body "## Initial Minimal Draft for univ8.eth EIP

This is an initial minimal draft submitted to start the review and CI feedback cycles for the univ8.eth proposal.

### Status
- ✅ Basic local tests executed
- 📝 Initial EIP structure created following EIP-1 requirements
- 🔄 Further tests, reference implementation, and optimizations will follow in subsequent commits

### Related Information
- **Fork PR**: https://github.com/leeli01284-collab/EIPs/pull/4
- **Author**: leeli01284-collab (0x4b064115af4a16192cbbf0e0111a2417d0cf494b)
- **File added**: \`EIPS/eip-draft_univ8-eth.md\`

### Next Steps
Follow-up commits will add:
- Complete specification details
- Full test suites under \`assets/eip-####/\`
- Reference implementation
- CI/CD workflow integration"
```

### PR Title and Body

**Title:**
```
EIP draft: univ8.eth (initial minimal draft)
```

**Body:**
```markdown
## Initial Minimal Draft for univ8.eth EIP

This is an initial minimal draft submitted to start the review and CI feedback cycles for the univ8.eth proposal.

### Status
- ✅ Basic local tests executed
- 📝 Initial EIP structure created following EIP-1 requirements
- 🔄 Further tests, reference implementation, and optimizations will follow in subsequent commits

### Related Information
- **Fork PR**: https://github.com/leeli01284-collab/EIPs/pull/4
- **Author**: leeli01284-collab (0x4b064115af4a16192cbbf0e0111a2417d0cf494b)
- **File added**: `EIPS/eip-draft_univ8-eth.md`

### Next Steps
Follow-up commits will add:
- Complete specification details
- Full test suites under `assets/eip-####/`
- Reference implementation
- CI/CD workflow integration
```

### Step 3: Mark as Ready for Review

After creating the PR:
1. If it's created as a draft, click **"Ready for review"** to make it reviewable
2. The PR will now be visible to ethereum/EIPs maintainers

### Troubleshooting

**Branch not found:**
- Ensure you pushed the branch: `git push -u origin eip-draft-univ8-eth-initial`
- Verify with: `git ls-remote origin eip-draft-univ8-eth-initial`

**Authentication failed:**
- For HTTPS: Use a Personal Access Token with `repo` scope
- For SSH: Ensure your SSH key is added to GitHub
- Check CLI auth: `gh auth status`

**Cannot create PR:**
- You don't need write access to ethereum/EIPs
- GitHub allows PRs from forks without upstream write access
- Ensure you selected the correct fork in the dropdown

### Summary

This will create a cross-repo PR that:
- Adds the file `EIPS/eip-draft_univ8-eth.md` to ethereum/EIPs
- Includes all required information per the problem statement
- Is marked as "Ready for review" (not draft)
- Contains proper references to the fork PR and author

Once created, ethereum/EIPs maintainers can review and provide feedback on the proposal.
