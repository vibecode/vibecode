---
name: vibecode
description: Build and change iPhone apps and web apps with Vibecode. Use when the user wants to make an app, change an app they built in Vibecode, check on a build, run commands in an app or deploy it, or find out why their Vibecode app isn't working.
---

# Vibecode

Vibecode's agent writes, builds and tests apps in the user's Vibecode account. These tools start that work, follow it and look inside the app. Every tool acts on the account the user connected.

## Building and changing
- To make a new app, call `create_app` with a clear brief: what the app is for, its screens, and anything the user asked for. A build usually takes about 10 minutes; a new app with a backend (full-stack) can take about 30.
- To change an app, call `edit_app`. If the agent is still working on that app, the change waits its turn and starts by itself.
- After either, call `wait_for_build` again and again until it reports the app is ready or the build stopped, then tell the user. Each call returns after a short wait with the build's stage, so a long build takes many calls; that's normal.
- `get_build_status` answers at once, without waiting.
- `show_app` and `get_handoff_links` give links to open the app in Vibecode, on the user's iPhone, or to publish it to the App Store from Vibecode.

## Following the agent
- `get_activity` shows what the agent did and why a build failed.
- `stop_build` stops the agent's current work and anything waiting behind it. Ask the user first.

## When something isn't working
- `get_logs` reads the app's logs: the workspace's while it runs, or the published backend's (`where: live`).
- `list_files` and `read_file` show the app's code. `.env` files can't be read, and keys in any output are hidden.
- `get_screenshot` shows the app's latest screenshot.

## Running commands
ChatGPT and Claude (claude.ai) don't have these tools; coding agents and other MCP apps do.
- `run_command` runs a bash command in the app's workspace, a Linux sandbox in the app's folder, and returns the output with the app's keys hidden. A command can be up to 20,000 characters. For a longer script, write it to a file over a few commands, then run the file.
- Use it to run tests, check versions, install a package, or make a small fix. For a feature or a design change, use `edit_app`, so Vibecode's agent makes and tests it.
- On Free, each `run_command` call counts toward 50 a week, reset Monday 00:00 UTC, and a command stops after 45 seconds. Put related checks in one command. When 10 or fewer are left, the answer says how many. At 0 it doesn't run and gives a plans link: pass it on. Reading files and logs doesn't count. Plus, Pro and Max have no weekly limit.
- On Plus, Pro and Max, a command keeps running for up to 20 minutes. `run_command` waits about 40 seconds; if the answer has status `running`, it gives a `command_id` and the output so far. Call `get_command_output` with the `project_id` and that `command_id` until it returns an exit code. Each call waits up to about 40 seconds and returns only the new output. Follow the running command this way rather than running it again.
- When a command ends, anything it started that still prints into its output is stopped. To leave a server running, send its output to a file: `nohup <command> > server.log 2>&1 &`.
- If `get_command_output` says the command is lost, the workspace restarted. Check what the command already changed before retrying: run it again only if it is safe to repeat, otherwise finish just the remaining work.
- `run_live_command` runs a command on the deployed app's live server (paid plans), in its backend folder, with real users' data. It backs up the live database first (the user can restore it from the app's Database tab), takes up to 4,000 characters and stops after 45 seconds. Run only what the user asked for, and change tables and columns through the app's Prisma schema and a deploy. On Free it answers that it needs a plan, with a link to pass on.

## Deploying
- `get_deployment` says whether the app is live and at what address, whether its server is answering, whether newer saved versions aren't live yet, and why the last deploy failed.
- `deploy_app` puts the app online, like Vibecode's Deploy button: a web app's site, or the server behind a mobile or iPhone app. It first saves edits made in the workspace (with `run_command`, say) as a new version, then deploys that. It never starts a charge: when deploying would start a trial or a charge, it deploys nothing and returns a link, so pass that on: there the user sees the price and confirms, or, on Free, picks a plan. After it starts, call `get_deployment` to see when it's live.
- If `deploy_app` says the workspace and the saved versions have diverged, run the git command it gives with `run_command`, then deploy again.
- `set_address` gives a web app its name.vibecode.run address (chosen once) or connects the user's own domain: it returns the DNS records to add, and calling again with the same domain checks them.
- `set_web_password` turns password protection of a web app's site on or off. It takes effect at the next deploy. Ask the user for the username and password; never make one up.
- To put an earlier version live, `restore_version` first, then `deploy_app`.

## Versions
- `list_versions` lists the app's saved versions.
- `restore_version` brings an earlier version back as a new version, so later versions stay and the restore can be undone. Ask the user first.

## Managing apps
- `list_projects` finds the user's apps. Refer to apps by name; never show project ids to the user.
- `rename_app` and `duplicate_app` change only the app named.
- `delete_app` removes the app from Vibecode, and only Vibecode support can bring it back. Use it only when the user asks, and confirm the app's name with them first.

## Account and credits
- `get_profile` names the connected account, its plan and its credits.
- Builds and changes use Vibecode credits. When a tool says the account needs a plan or more credits, pass on its link: plans and credits are managed on vibecodeapp.com, and nothing is sold in the chat.
