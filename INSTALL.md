# Agent installation and project setup instructions

These instructions are for the agent setting up Ticket Recall in a software project. Setup prepares ticket access only. Do not edit, comment on, transition, assign, label, close, or otherwise change a ticket during setup.

## 1. Make the skills available

The project contains these skill folders under `.agents/skills`:

- `ticket-update`
- `ticket-reconstruct`
- `ticket-review`

If the current agent harness discovers Agent Skills from `.agents/skills`, use them in place. Otherwise, copy each complete folder into the harness's configured skills directory. Keep each `SKILL.md` inside its skill folder.

## 2. Identify the tracker and operating system

Inspect repository remotes, issue templates, contribution docs, existing ticket links, and user-supplied context.

- Use `gh` for GitHub Issues.
- Use `acli` for Jira Cloud.
- An installed CLI is only a clue; it does not prove which tracker the project uses.
- If the tracker is ambiguous, ask the user whether the team uses GitHub Issues or Jira before installing anything.

Detect whether the machine runs Windows, macOS, or Linux and which package manager is available. Assume a capable package manager is already installed; do not install or configure a package manager.

Check whether the selected CLI already exists:

```sh
gh --version
acli --version
```

Run only the command for the selected tracker. If the CLI is already installed, skip installation.

## 3. Ask permission before installing

Before running an installation command:

1. State the selected tracker and detected operating system.
2. Show the exact installation command you intend to run.
3. Ask the user for permission to proceed.

Do not install until permission is granted. Permission for one command does not authorize a different installer or additional system changes.

## 4. Install GitHub CLI (`gh`)

Choose the single command that matches the user's operating system and package manager. See the [GitHub CLI installation documentation](https://github.com/cli/cli#installation).

### Windows

```powershell
winget install --exact --id GitHub.cli --source winget
```

### macOS

```sh
brew install gh
```

### Debian or Ubuntu Linux

```sh
sudo apt update && sudo apt install -y gh
```

### Fedora or RHEL Linux

```sh
sudo dnf install -y gh
```

### Amazon Linux

```sh
sudo yum install -y gh
```

### openSUSE or SUSE Linux

```sh
sudo zypper install -y gh
```

### Arch Linux

```sh
sudo pacman -S --noconfirm github-cli
```

Verify after installation:

```sh
gh --version
```

## 5. Install Atlassian CLI (`acli`)

Choose the single command block that matches the user's operating system and package manager. See the [Atlassian CLI installation documentation](https://developer.atlassian.com/cloud/acli/guides/install-acli/) and [supported packages](https://developer.atlassian.com/cloud/acli/guides/download-supported-packages/).

### Windows

The current WinGet package identifier is `Atlassian.AtlassianCLI`.

```powershell
winget install --exact --id Atlassian.AtlassianCLI --source winget
```

### macOS

```sh
brew tap atlassian/homebrew-acli
brew install acli
```

### Debian or Ubuntu Linux

```sh
acli_arch="$(dpkg --print-architecture)"
curl -fL "https://acli.atlassian.com/linux/latest/acli_linux_${acli_arch}.deb" -o acli.deb
sudo apt install -y ./acli.deb
```

### Fedora or RHEL Linux

```sh
acli_arch="$(uname -m | sed -e 's/^x86_64$/amd64/' -e 's/^aarch64$/arm64/')"
curl -fL "https://acli.atlassian.com/linux/latest/acli_linux_${acli_arch}.rpm" -o acli.rpm
sudo dnf install -y ./acli.rpm
```

### Amazon Linux

```sh
acli_arch="$(uname -m | sed -e 's/^x86_64$/amd64/' -e 's/^aarch64$/arm64/')"
curl -fL "https://acli.atlassian.com/linux/latest/acli_linux_${acli_arch}.rpm" -o acli.rpm
sudo yum localinstall -y ./acli.rpm
```

### openSUSE or SUSE Linux

```sh
acli_arch="$(uname -m | sed -e 's/^x86_64$/amd64/' -e 's/^aarch64$/arm64/')"
curl -fL "https://acli.atlassian.com/linux/latest/acli_linux_${acli_arch}.rpm" -o acli.rpm
sudo zypper install -y ./acli.rpm
```

Verify after installation:

```sh
acli --version
```

## 6. Authenticate with user participation

Authentication is interactive. Never ask the user to paste a password or token into chat, print secrets, or store secrets in the project.

### GitHub

Check status:

```sh
gh auth status
```

If authentication is required, tell the user an interactive login will begin, then run:

```sh
gh auth login
```

Let the user complete the browser or device flow. Verify again with `gh auth status`.

### Jira Cloud

Check status:

```sh
acli jira auth status
```

If authentication is required, tell the user a browser-based login will begin, then run:

```sh
acli jira auth login --web
```

Tell the user to complete browser consent and select the same Jira site in the terminal. Verify again with `acli jira auth status`. If Atlassian reports that a site administrator must authorize the application, stop and report that administrator action is required.

## 7. Verify the correct project with read-only commands

For GitHub, run from the target repository:

```sh
gh repo view --json nameWithOwner,url
```

For Jira, ask the user for the project key if it is not already clear:

```sh
acli jira project view --key "PROJECT_KEY" --json
```

If the Jira project key is unknown, list visible projects:

```sh
acli jira project list --limit 50 --json
```

Setup is complete only when the selected CLI is installed, authentication succeeds, and the agent can read the correct repository or Jira project. Report the tracker, CLI version, authenticated host or site, and verified target. Then stop without updating a ticket.
