# Instructions for Creating Cross-Repo Pull Request to ethereum/EIPs

## Overview
This document provides step-by-step instructions for creating a pull request from the fork `leeli01284-collab/EIPs` to the upstream `ethereum/EIPs` repository with the univ8.eth EIP draft.

## Important Information
- **Fork repository**: leeli01284-collab/EIPs
- **Upstream repository**: ethereum/EIPs  
- **Source branch**: eip-draft-univ8-eth-initial
- **Target branch**: main (in ethereum/EIPs)
- **PR Title**: EIP draft: univ8.eth (initial minimal draft)
- **Related fork PR**: https://github.com/leeli01284-collab/EIPs/pull/4
- **Author**: leeli01284-collab (0x4b064115af4a16192cbbf0e0111a2417d0cf494b)

## Prerequisites
- You must have push access to the `leeli01284-collab/EIPs` repository
- You must be authenticated with GitHub (either via web or CLI)

## Step 1: Push the Branch to GitHub

First, push the local branch `eip-draft-univ8-eth-initial` to the fork:

```bash
# Ensure you're on the correct branch
git checkout eip-draft-univ8-eth-initial

# Push the branch to origin
git push -u origin eip-draft-univ8-eth-initial
```

After pushing, verify the branch exists on GitHub:
```bash
git ls-remote origin eip-draft-univ8-eth-initial
```

## Step 2: Create the Pull Request

You can create the PR using either the GitHub Web UI or the GitHub CLI (`gh`).

### Option A: Using GitHub Web UI

1. **Navigate to the upstream repository**:
   - Go to https://github.com/ethereum/EIPs

2. **Click "Pull requests"** tab

3. **Click "New pull request"** button

4. **Click "compare across forks"** link (appears near the top of the page, to the right of "Comparing changes")

5. **Select the repositories and branches**:
   - **Base repository**: `ethereum/EIPs`
   - **Base branch**: `main`
   - **Head repository**: `leeli01284-collab/EIPs`
   - **Compare branch**: `eip-draft-univ8-eth-initial`

6. **Review the changes** shown in the diff viewer (should show the new EIP file)

7. **Click "Create pull request"** button

8. **Fill in the PR details** (see Step 3 below)

### Option B: Using GitHub CLI

If you have the GitHub CLI (`gh`) installed and authenticated:

```bash
# Make sure you're on the branch
git checkout eip-draft-univ8-eth-initial

# Create the PR
gh pr create \
  --repo ethereum/EIPs \
  --base main \
  --head leeli01284-collab:eip-draft-univ8-eth-initial \
  --title "EIP draft: univ8.eth (initial minimal draft)" \
  --body-file - <<'EOF'
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

### What's Included
This minimal draft contains:
- Preamble with proposal metadata (title, description, author, type: Informational)
- Required sections per EIP-1: Abstract, Motivation, Specification, Rationale, Backwards Compatibility, Test Cases, Reference Implementation, Security Considerations, Copyright
- Placeholder content indicating detailed specification, tests, and reference implementation will follow

### Next Steps
Follow-up commits will add:
- Complete specification details
- Full test suites under `assets/eip-####/`
- Reference implementation
- CI/CD workflow integration
EOF
```

## Step 3: PR Title and Description

Use the following exact content when creating the PR:

**Title:**
```
EIP draft: univ8.eth (initial minimal draft)
```

**Description:**
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

### What's Included
This minimal draft contains:
- Preamble with proposal metadata (title, description, author, type: Informational)
- Required sections per EIP-1: Abstract, Motivation, Specification, Rationale, Backwards Compatibility, Test Cases, Reference Implementation, Security Considerations, Copyright
- Placeholder content indicating detailed specification, tests, and reference implementation will follow

### Next Steps
Follow-up commits will add:
- Complete specification details
- Full test suites under `assets/eip-####/`
- Reference implementation
- CI/CD workflow integration
```

## Step 4: Mark as Ready for Review

After creating the PR:

1. If the PR is created as a **draft** by default:
   - Go to the PR page on GitHub
   - Scroll down to find the **"Ready for review"** button
   - Click it to convert the PR to a normal (reviewable) PR

2. The PR should now be visible to ethereum/EIPs maintainers and ready for review

## Troubleshooting

### Branch Not Found on Remote
If you get an error that the branch doesn't exist on the remote:
1. Verify you pushed it: `git ls-remote origin eip-draft-univ8-eth-initial`
2. If not present, push it as shown in Step 1

### Authentication Failed
If you get authentication errors when pushing:
- For HTTPS: Ensure you're using a Personal Access Token (classic) with `repo` scope, not your password
- For SSH: Ensure your SSH key is added to your GitHub account
- Run `gh auth status` to check GitHub CLI authentication

### Permission Denied Creating PR
This is normal - you don't need write access to ethereum/EIPs to create a PR:
- GitHub allows creating PRs from forks even without write access to the upstream
- Make sure you're selecting the correct repositories in the fork selection dropdown
- The "head repository" should be `leeli01284-collab/EIPs`
- The "base repository" should be `ethereum/EIPs`

### PR Shows as Draft
If the PR is created as a draft by default:
1. Go to the PR page on GitHub
2. Scroll down to find the "Ready for review" button  
3. Click it to convert the PR to a regular (reviewable) PR

### Cannot See "Compare Across Forks" Link
If you don't see the "compare across forks" link:
1. Make sure you're on the ethereum/EIPs repository (not your fork)
2. The link appears after clicking "New pull request"
3. It should be near the repository/branch selectors at the top

## Verification

After creating the PR, verify:
- ✅ PR title is: "EIP draft: univ8.eth (initial minimal draft)"
- ✅ PR is against ethereum/EIPs `main` branch
- ✅ PR shows the `EIPS/eip-draft_univ8-eth.md` file being added
- ✅ PR is marked as "Ready for review" (not draft)
- ✅ PR description includes the fork PR link and author information

## Summary

The cross-repo PR will:
- **Source**: leeli01284-collab/EIPs branch `eip-draft-univ8-eth-initial`
- **Target**: ethereum/EIPs branch `main`  
- **Content**: Add `EIPS/eip-draft_univ8-eth.md` with initial minimal draft
- **Purpose**: Start review and CI feedback cycles
- **Status**: Ready for review

Once the PR is created and marked as ready for review, the ethereum/EIPs maintainers will be able to review it and provide feedback.
