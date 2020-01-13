# Sync github labels

#### Dependency

[github-label-sync](https://www.npmjs.com/package/github-label-sync)

#### Instructions

Set up local variables

```
export SYNC_ROOT_PATH="~/src/"
export SYNC_FILE_NAME="gitLabels.json"
export GITHUB_USER="[username]"
```

Requires local Personal Access Token sync with Github

#### CLI command

```
github-label-sync --access-token $GITHUB_TOKEN --labels $SYNC_ROOT_PATH/$SYNC_FILE_NAME $GITHUB_USER/[repo]
```
