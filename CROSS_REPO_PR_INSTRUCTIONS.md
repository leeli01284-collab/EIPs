# Instructions for Creating Cross-Repo Pull Request

## ⚠️ IMPORTANT: First Step Required
**Before creating the PR, you MUST push the branch `eip-draft-univ8-eth-initial` to GitHub:**
```bash
cd /home/runner/work/EIPs/EIPs
git checkout eip-draft-univ8-eth-initial
git push -u origin eip-draft-univ8-eth-initial
```

## Overview
This document provides instructions for creating a pull request from the fork `leeli01284-collab/EIPs` to the upstream `ethereum/EIPs` repository.

## Background
- **Fork repository**: leeli01284-collab/EIPs
- **Upstream repository**: ethereum/EIPs
- **Source branch**: eip-draft-univ8-eth-initial
- **Target branch**: main (in ethereum/EIPs)
- **Related fork PR**: https://github.com/leeli01284-collab/EIPs/pull/4

## Steps to Create the Cross-Repo PR

### Prerequisites
- You must have push access to the `leeli01284-collab/EIPs` repository
- The branch `eip-draft-univ8-eth-initial` must exist in the fork with the EIP draft content

### Step 1: Push the Branch (REQUIRED FIRST STEP)
The branch `eip-draft-univ8-eth-initial` exists locally but needs to be pushed to the fork:

```bash
# In your local clone of leeli01284-collab/EIPs
cd /home/runner/work/EIPs/EIPs
git checkout eip-draft-univ8-eth-initial
git push -u origin eip-draft-univ8-eth-initial
```

Verify the branch was pushed successfully:
```bash
git ls-remote origin | grep eip-draft-univ8-eth-initial
```

You should see output like:
```
<sha>	refs/heads/eip-draft-univ8-eth-initial
```

### Step 2: Verify Branch is Pushed
After pushing, verify the branch appears on GitHub:
1. Go to https://github.com/leeli01284-collab/EIPs/branches
2. Look for `eip-draft-univ8-eth-initial` in the list
3. Or check via API: `curl -s https://api.github.com/repos/leeli01284-collab/EIPs/branches | grep eip-draft-univ8-eth-initial`

### Step 3: Create the Pull Request via GitHub Web UI

1. **Navigate to the upstream repository**:
   Go to https://github.com/ethereum/EIPs

2. **Click "Pull requests"** tab

3. **Click "New pull request"** button

4. **Click "compare across forks"** link (near the top of the page)

5. **Select the repositories and branches**:
   - **Base repository**: `ethereum/EIPs`
   - **Base branch**: `main`
   - **Head repository**: `leeli01284-collab/EIPs`
   - **Compare branch**: `eip-draft-univ8-eth-initial`

6. **Click "Create pull request"**

### Step 4: Fill in PR Details

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

### Expected Validation Issues
The following are expected to be resolved during the editor review process:
- Missing `eip` number field (to be assigned by editors)
- Author format uses Ethereum address instead of GitHub username
- Missing `discussions-to` URL (forum thread TBD)
- Filename/number mismatch (intentional for draft stage)

### Next Steps
Follow-up commits will add:
- Complete specification details
- Full test suites under `assets/eip-####/`
- Reference implementation
- CI/CD workflow integration
```

### Step 4: Mark as Ready for Review

After creating the PR:
1. If the PR is created as a draft, click the **"Ready for review"** button to convert it to a normal PR
2. This ensures the PR is visible to maintainers and can be reviewed

### Alternative: Using GitHub CLI

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
  --body "$(cat <<'EOF'
## Initial Minimal Draft for univ8.eth EIP

This is an initial minimal draft submitted to start the review and CI feedback cycles for the univ8.eth proposal.

### Status
- ✅ Basic local tests executed
- 📝 Initial EIP structure created following EIP-1 requirements
- 🔄 Further tests, reference implementation, and optimizations will follow in subsequent commits

### Related Information
- **Fork PR**: https://github.com/leeli01284-collab/EIPs/pull/4
- **Author**: leeli01284-collab (0x4b064115af4a16192cbbf0e0111a2417d0cf494b)
- **File added**: EIPS/eip-draft_univ8-eth.md

### What's Included
This minimal draft contains:
- Preamble with proposal metadata (title, description, author, type: Informational)
- Required sections per EIP-1: Abstract, Motivation, Specification, Rationale, Backwards Compatibility, Test Cases, Reference Implementation, Security Considerations, Copyright
- Placeholder content indicating detailed specification, tests, and reference implementation will follow

### Expected Validation Issues
The following are expected to be resolved during the editor review process:
- Missing eip number field (to be assigned by editors)
- Author format uses Ethereum address instead of GitHub username
- Missing discussions-to URL (forum thread TBD)
- Filename/number mismatch (intentional for draft stage)

### Next Steps
Follow-up commits will add:
- Complete specification details
- Full test suites under assets/eip-####/
- Reference implementation
- CI/CD workflow integration
EOF
)"

# If the command succeeds, you can check the PR URL it returns
```

**Note**: Before running this command, ensure you've completed Step 1 (pushing the branch).

**Note**: Before running this command, ensure you've completed Step 1 (pushing the branch).

## Troubleshooting

### Branch Not Pushed Yet
If you get an error that the branch doesn't exist when creating the PR:
1. Complete Step 1 first (push the branch)
2. Verify the push was successful: `git ls-remote origin eip-draft-univ8-eth-initial`
3. If still not showing, wait a minute for GitHub to update, then try again

### Branch Not Found
If you get an error that the branch doesn't exist:
1. Verify the branch exists: `git ls-remote origin eip-draft-univ8-eth-initial`
2. If not, create and push it as shown in Step 1

### Permission Denied
If you cannot create a PR to ethereum/EIPs:
- This is expected if you don't have write access to the upstream repository
- GitHub allows creating PRs from forks even without write access to the upstream
- Make sure you're selecting the correct repositories in the fork selection dropdown

### PR Shows as Draft
If the PR is created as a draft by default:
1. Go to the PR page
2. Scroll down to find the "Ready for review" button
3. Click it to convert the PR to a regular (reviewable) PR

## Summary

The key information needed:
- **Source**: leeli01284-collab/EIPs branch eip-draft-univ8-eth-initial
- **Target**: ethereum/EIPs branch main
- **Title**: EIP draft: univ8.eth (initial minimal draft)
- **Status**: Ready for review (not draft)
- **Author**: leeli01284-collab (0x4b064115af4a16192cbbf0e0111a2417d0cf494b)
- **Fork PR**: https://github.com/leeli01284-collab/EIPs/pull/4
