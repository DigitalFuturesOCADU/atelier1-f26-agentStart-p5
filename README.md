# p5 Phone Agent Start

A starting point for p5.js sketches on your phone, set up for working with a coding agent: OpenCode, or the Chat in VS Code.

It has everything in the simple starter (`index.html`, `sketch.js`, the skills), plus four things for working with an agent: notes the agent reads every session, a plan you fill in, a folder for your references, and a command that shows your sketch on your phone without pushing.

## What is in it

| File | What it does | Who writes it |
|---|---|---|
| `index.html` | Loads p5.js 2, p5-phone and your sketch. | Nobody, most of the time |
| `sketch.js` | Your sketch. | You and the agent |
| `plan.md` | What you want, and the steps to get there. | You, above Steps. The agent writes the Steps. |
| `references/` | The images your plan points to: layouts, inspiration, example code. | You |
| `AGENTS.md` | Notes the agent reads at the start of every session. | You. Change it as you learn how you like to work. |
| `.agents/skills/` | Two skills: how p5-phone works, and how to write p5.js 2. | Leave them as they are |
| `package.json`, `scripts/phone.mjs` | The phone command, `npm run phone`. | Leave them as they are |
| `README.md` | This page. | You, if you like |
| `.nojekyll`, `.gitignore`, `.vscode/` | Small settings for GitHub Pages, Git and VS Code. | Leave them as they are |

Files and folders that start with a dot are hidden in Finder and File Explorer. VS Code and GitHub show them.

## Use it

The full walkthrough with screenshots is here:
https://digitalfuturesocadu.github.io/vsCodeSetup/guide/

The short version:

1. Click **Use this template**, then **Create a new repository**. Keep it **Public**.
2. In your new repository, open **Settings**, then **Pages**. Under **Build and deployment**, leave **Source** on **Deploy from a branch**. Set **Branch** to **main** and the folder to **/ (root)**, then click **Save**. After that, every push publishes your sketch.
3. In VS Code, choose **Clone Git Repository**, then **Clone from GitHub**, and pick your new repository.
4. Open `index.html` and click **Go Live** to see the sketch on your laptop.
5. Change `sketch.js`. In Source Control, write a message, click **Commit**, then **Sync Changes**.
6. Wait about a minute. Open this address on your phone:

```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

GitHub does not copy the Pages setting from the template, so each new copy needs step 2 once. Until then, your address shows a 404. You do not need GitHub Actions, and you do not need the **Configure** button.

## Start a plan

1. Open `plan.md`. Fill in everything above **Steps** yourself. Rough notes are fine.
2. Put any images you mention in `references/`, and list them in the References table.
3. Commit.
4. In OpenCode, choose **Plan** and send:

```
@plan.md Read my plan and open each image in references. Write the Steps: small steps, each one I can check on my phone. Then list what you had to assume. Do not change any files.
```

5. Read the steps and cut them down. Anything it had to assume is a decision it made for you. If you care about one, add it to the top of your plan.
6. Plan cannot edit your files. Switch to **Build** and send: `Put those steps under Steps in plan.md. Change nothing else.` Commit.
7. Still in **Build**, send: `Do step 1.` Check it on your phone. Commit if you keep it.

If your plan is still thin, start with this in **Plan** instead:

```
@plan.md Read my plan. Ask me questions about anything that is unclear, one at a time, up to five. Do not write the steps yet. Do not change any files.
```

In VS Code's Chat the same steps work. Choose **Plan**, then **Agent**, and type `#` to point at `plan.md`.

## See it on your phone without pushing

`npm run phone` opens a temporary HTTPS address for Live Server and prints a QR code. Tilt, shake and sound work on the phone, and every save shows up when you reload.

It needs two installs, once:

- **Node.js**, the LTS version from nodejs.org.
- **cloudflared**. Mac: `brew install cloudflared`. Windows: `winget install --id Cloudflare.cloudflared`.

Then, each time:

1. Click **Go Live** in VS Code. Live Server runs on port 5500.
2. Open a terminal in this folder (in VS Code or OpenCode) and run `npm run phone`.
3. Scan the QR code. Press `Ctrl+C` to stop. The address changes next time.

Anyone with the address can open it while it runs. For anything you hand in or show, use Pages.

## Already have a repo?

If you made your repo from the simple starter, you can add these pieces to it. Commit first. Then open your project in OpenCode, choose **Build**, and paste:

```
Copy these from the template at github.com/DigitalFuturesOCADU/atelier1-f26-agentStart-p5 into this project: AGENTS.md, plan.md, the references folder, package.json, and the scripts folder. If .agents/skills is missing here, copy that too. If a file already exists here, do not replace it. Tell me instead. Do not change any of my other files, and do not commit. Then list what you added.
```

Look at what changed in the Review panel or in Source Control. Then commit.

## If your page does not publish

Ask your coding agent. In OpenCode, or in VS Code's Chat set to **Agent**, open this project and paste the prompt below. It needs the GitHub CLI signed in first: run `gh auth login`.

```
Turn on GitHub Pages for this repo so it publishes from the main branch. Use the GitHub CLI. Run gh api -X POST "repos/{owner}/{repo}/pages" -f "source[branch]=main" -f "source[path]=/". If it says Pages is already enabled, run gh api -X PUT "repos/{owner}/{repo}/pages" -f build_type=legacy -f "source[branch]=main" -f "source[path]=/" instead. Then find the newest run with gh run list --limit 1, follow it with gh run watch and its ID, and when it finishes tell me the Pages address from gh api "repos/{owner}/{repo}/pages" --jq .html_url.
```

The same fix is in the setup guide, with a Copy button for the prompt: [Pages is not switched on](https://digitalfuturesocadu.github.io/vsCodeSetup/guide/#fix--pages-off).

## Skills for your coding agent

The `.agents/skills` folder holds two skills. A skill is a set of notes a coding agent reads when it needs them. OpenCode and the Chat in VS Code both look in this folder.

- `p5-phone` explains how p5-phone reaches the phone's sensors and asks for permissions.
- `p5js-2x` keeps the agent writing p5.js 2.x code, not the older 1.x code most models learned from.

`AGENTS.md` asks the agent to load both before it starts. They come from the [p5-phone repository](https://github.com/npuckett/p5-phone). Leave them as they are for now. You can add your own skills next to them later.
