## ne14.library.standards
``` bash
# Upload to local package repo
$ver="1.0.0-alpha-0001"; dotnet pack -c Release -o nu -p:Version=$ver; dotnet nuget push "nu\*standards*.$ver.nupkg" --source localdev
```

# GitHub Account Setup
  1. Create a new PAT (1 per account): `Account > Settings > Developer Settings > Personal Access Tokens`
  1. Provide read:packages to it
  1. Add nuget feed in your local %APPDATA%/NuGet/NuGet.Config

# GitHub Repo Setup
  1. Generate a new SSH Key Pair
  1. Add a Deploy Key called `COMMIT_KEY_PUB` containing the public part of the SSH key (do give write access)
  1. Add a Secret called `COMMIT_KEY` containing the private part of the SSH key
  1. Add a Secret called `READ_REPO_PACKAGES` containing the *packages:read* central PAT Token
  1. Ensure csproj in your package project has correct <VersionPrefix> and <RepoUrlStyle> tags
  1. Ensure repo workflows have read and write permissions: `Repo > Settings > Actions > Workflow permissions`