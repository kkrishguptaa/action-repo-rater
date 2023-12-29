<div align="center">
  <img src="https://github.com/EddieHubCommunity.png" height="100px" width="100px" style="border-radius: 100%;" />
  <br />
  <h1>Repo Rater Action</h1>
  <p>Get votes on <a href="https://repo-rater.eddiehub.io">EddieHub Repo Rater</a> without lifting a finger 🌟</p>
</div>

## ❓ Why `action-repo-rater`?

- 🍭 Get votes on your repository without lifting a finger
- 🐙 Automatically comment on issues and pull requests to get votes
- 🤖 Rank up on the [EddieHub Repo Rater](https://repo-rater.eddiehub.io)

## 📦 Usage

### Allow github-actions to create comments

1. Go to Settings -> Actions
   
   <img width="1582" alt="GitHub Action Settings Page" src="https://github.com/xkrishguptaa/action-repo-rater/assets/135469703/bbff3611-9085-4904-855e-7abd05433bef">

2. Enable `write` permission for GitHub Actions
   
   <img width="1582" alt="image" src="https://github.com/xkrishguptaa/action-repo-rater/assets/135469703/3888f62e-9606-4ac5-a2d7-6ab5cb9bad55">

### Creation Action File

Create a file called `.github/workflows/repo-rater.yml

```yml
name: repo-rater
run-name: repo-rater (#${{ github.event.issue.number || github.event.pull_request.number }})

on:
  issues:
    types: [closed]
  pull_request:
    types: [closed]

jobs:
  repo-rater:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: xkrishguptaa/action-repo-rater@v1
```

## 📝 Configuration

| Key               | Description                                                                 | Required | Default Value |
| ----------------- | --------------------------------------------------------------------------- | -------- | ------------- |
| github-token      | The GitHub token to use for authentication, Use this if you want the comment to be posted a user rather than `github-actions` | false | `${{ github.token }}` |
| message           | The message to post on the issue or pull request                              | false    | `Thank you all for contributing to this repo! Please take a moment to rate its DX on [EddieHub Repo Rater](https://repo-rater.eddiehub.io/rate?owner=${{ github.repository_owner }}&name=${{ github.event.repository.name }}) and star it 💓` |
