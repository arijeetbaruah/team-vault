\# Team Vault



Shared Obsidian vault for our team project. We use the \*\*Operon\*\* plugin for task management and the \*\*Obsidian Git\*\* plugin to sync this vault through GitHub.



Repo: https://github.com/arijeetbaruah/team-vault



\---



\## 1. Prerequisites



Install the following on your computer:



\- \[Obsidian](https://obsidian.md/download)

\- \[Git](https://git-scm.com/downloads). Check it with `git --version` in a terminal.

\- A GitHub account that has been \*\*added as a collaborator\*\* on this repo (ask the repo owner).



Set your git identity (once per machine):



```bash

git config --global user.name "Your Name"

git config --global user.email "you@example.com"

```



\---



\## 2. Set up GitHub authentication



Pick \*\*one\*\* option. Confirm it works in a terminal before using Obsidian.



\### Option A: SSH key (recommended)



1\. Generate a key (press Enter through the prompts):

&#x20;  ```bash

&#x20;  ssh-keygen -t ed25519 -C "you@example.com"

&#x20;  ```

2\. Copy the public key:

&#x20;  ```bash

&#x20;  cat \~/.ssh/id\_ed25519.pub

&#x20;  ```

&#x20;  (Windows PowerShell: `type $env:USERPROFILE\\.ssh\\id\_ed25519.pub`)

3\. On GitHub, go to \*\*Settings → SSH and GPG keys → New SSH key\*\* and paste it.

4\. Test the connection:

&#x20;  ```bash

&#x20;  ssh -T git@github.com

&#x20;  ```



\### Option B: HTTPS with a Personal Access Token



1\. On GitHub, go to \*\*Settings → Developer settings → Personal access tokens\*\* and create a token with the `repo` scope.

2\. Use the token as your password the first time git asks for credentials. Git Credential Manager (included with Git on Windows and macOS) will remember it.



\---



\## 3. Clone the vault



\*\*SSH:\*\*

```bash

git clone git@github.com:arijeetbaruah/team-vault.git

```



\*\*HTTPS:\*\*

```bash

git clone https://github.com/arijeetbaruah/team-vault.git

```



Clone it to a normal local folder (for example `\~/Documents/team-vault`). Avoid placing it inside iCloud, Dropbox or OneDrive, since two sync systems on one folder cause conflicts.



\---



\## 4. Open it in Obsidian



1\. Open Obsidian.

2\. Click \*\*Open folder as vault\*\*.

3\. Select the `team-vault` folder you just cloned.

4\. When prompted, choose \*\*Trust author and enable plugins\*\*.



\---



\## 5. Install the plugins



Go to \*\*Settings → Community plugins\*\*, turn off \*\*Restricted mode\*\*, then:



\### Obsidian Git

1\. Click \*\*Browse\*\*, search for \*\*Git\*\* (by Vinzent), then \*\*Install\*\* and \*\*Enable\*\*.



\### Operon

Operon is installed from GitHub rather than the Community Plugins directory:



1\. Follow the install steps in the \[Operon README](https://github.com/hasanyilmaz/operon) (typically via the \*\*BRAT\*\* plugin, or by downloading a release into `.obsidian/plugins/operon/`).

2\. Enable \*\*Operon\*\* under \*\*Settings → Community plugins\*\*.



> \*\*Important:\*\* Everyone on the team must use the \*\*same Operon version\*\*. Do not update Operon on your own. Ask the team first.



\---



\## 6. Configure Obsidian Git



Open \*\*Settings → Git\*\* and set:



| Setting | Value |

|---|---|

| Auto commit-and-sync interval (minutes) | `10` |

| Auto pull interval (minutes) | `5` |

| Pull on startup | \*\*On\*\* |

| Sync method | \*\*Merge\*\* |

| Pull before push | \*\*On\*\* |

| Commit message | `vault backup: {{date}} by {{hostname}}` |

| Show status bar | \*\*On\*\* |



Test it: open the command palette (`Ctrl/Cmd + P`), run \*\*Git: Commit-and-sync\*\*, then check GitHub to confirm your commit appears.



\---



\## 7. Daily workflow



1\. Open Obsidian. It pulls the latest changes automatically on startup.

2\. Work normally. Obsidian Git commits and pushes on the interval you set.

3\. Before closing, run \*\*Git: Commit-and-sync\*\* so your latest edits are pushed.

4\. If you've been away for a while, run \*\*Git: Pull\*\* before you start.



Useful commands (`Ctrl/Cmd + P`):



\- \*\*Git: Commit-and-sync\*\*

\- \*\*Git: Pull\*\*

\- \*\*Git: Open source control view\*\*

\- \*\*Git: Open history view\*\*



\---



\## 8. Avoiding conflicts



\- Stick to your own notes and task files where possible. Don't edit the same file at the same time as a teammate.

\- Sync often, and pull before you start working.

\- Don't edit files directly on github.com. Always edit in Obsidian and sync.



\### If you get a merge conflict



1\. Open the conflicted file. You'll see markers like `<<<<<<<`, `=======` and `>>>>>>>`.

2\. Keep the content you want and delete the markers.

3\. Run \*\*Git: Commit-and-sync\*\*.

4\. If you're unsure, ask the teammate who edited the file.



\---



\## 9. What gets synced



The `.gitignore` excludes machine-specific files such as workspace layout and caches:



```

.obsidian/workspace.json

.obsidian/workspace-mobile.json

.obsidian/cache

.trash/

.DS\_Store

```



Plugin settings (including Operon's) are shared, so everyone sees the same configuration. Please don't change shared plugin settings without telling the team.



\---



\## 10. Troubleshooting



| Problem | Fix |

|---|---|

| "git not found" in Obsidian | Set the path in \*\*Settings → Git → Advanced → Git path\*\* (`which git`, or `where git` on Windows). |

| Obsidian Git hangs or asks for a password | Run `git pull` in a terminal inside the vault folder and sign in once so credentials are cached. |

| "Permission denied (publickey)" | Your SSH key isn't added to GitHub. Redo section 2, Option A. |

| "Repository not found" or 403 | You haven't been added as a collaborator. Ask the repo owner. |

| Obsidian installed via Snap (Linux) can't use git | Use the Flatpak or AppImage version instead. |

| Operon tasks look different from a teammate's | Check you're on the same Operon version and have pulled the latest changes. |



\*\*Mobile note:\*\* Obsidian Git is unreliable on iOS and limited on Android. Use a desktop for editing this vault.



\---



\## Questions?



Contact the repo owner: \[@arijeetbaruah](https://github.com/arijeetbaruah)

