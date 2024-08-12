# Integrating Wakatime with GitHub Actions

## Prerequisites:
- **Wakatime Account**: If you don't have a Wakatime account yet, sign up for a free account at [https://wakatime.com/](https://wakatime.com/). During signup, you'll be guided through creating an API key.
- **GitHub Repository**: Have the GitHub repository URL readily available.

## Steps:

### 1. Generate Wakatime API Key:
1. Log in to your Wakatime account.
2. Navigate to Settings > Secrets (or API Access depending on your Wakatime account version).
3. Click Create Secret or Add API Key.
4. Give your API key a descriptive name (e.g., "GitHub Actions Wakatime Integration").
5. Copy the generated API key. You'll need it later.

### 2. Create GitHub Personal Access Token (GH_TOKEN):
1. Sign in to your GitHub account.
2. Go to Settings > Developer settings > OAuth Apps.
3. Click New GitHub App.
4. Give your app a name (e.g., "Wakatime GitHub Actions Integration").
5. Choose a homepage URL (optional).
6. Under Select an app type, choose "OAuth Apps".
7. Click "Developer application".
8. Click Generate a secret for a new client secret. Copy the generated secret. You'll need it later.
9. Under "OAuth Apps", click "Authorization".
10. Select the repositories you want to grant access to (if applicable).
11. Under "Device & app permissions", select "repo" with read and write permissions (this allows the GitHub Actions workflow to interact with your repository).
12. Click "Save".

### 3. Fork the Repository:
1. Navigate to the desired GitHub repository you want to integrate with Wakatime.
2. Click the Fork button in the top right corner. This creates a copy of the repository in your own GitHub account.

### 4. Enable Workflow Permissions:
1. Go to your forked repository on GitHub.
2. Click on Settings.
3. Under "Advanced settings", navigate to "Actions".
4. In the "Workflow permissions" section, select "Read and write" permissions. This allows the GitHub Actions workflow to modify files in your repository.

### 5. Configure GitHub Actions Workflow:
#### Option 1: Using a Template (Recommended):
1. GitHub provides a ready-made Wakatime workflow template you can easily utilize.
2. In your forked repository, navigate to the `.github/workflows` directory (if it doesn't exist, create it).
3. Click on New file and name it `main.yml`.
4. Paste the following content into the file, replacing `<WAKAKATIME_API_KEY>` with your actual Wakatime API key:

```yaml
```bash
name: Update README with Wakatime Stats

on:
  push: {}

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: morangoice/wakatime-readme@v2.7.0  # Or the latest version
        with:
          api_key: ${{ secrets.WAKAKATIME_API_KEY }}
```
5.Save the file. This will trigger a workflow that automatically updates your repository's README with your Wakatime stats whenever you push changes.
