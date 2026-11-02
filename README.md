# Vibecode

[![skills.sh](https://skills.sh/b/vibecode/vibecode)](https://skills.sh/vibecode/vibecode)

[Vibecode](https://www.vibecodeapp.com) builds iPhone apps and web apps from a description. Vibecode's agent writes the app, builds it and tests it.

This repository holds the Vibecode plugin for Grok Bot, Claude Code and Gemini CLI, and it's where you can report Vibecode bugs and request features. Any other MCP app can connect to `https://api.vibecodeapp.com/mcp` directly ([setup guides](https://www.vibecodeapp.com/docs/guides/vibecode-mcp)).

## The Vibecode plugin

Build and change apps by chatting. From the chat you can follow a build, ask for changes, and look inside an app when something isn't working.

### Getting started

1. Install the Vibecode plugin:
   - **Grok Bot:** install Vibecode from the plugin marketplace and select **Connect**.
   - **Claude Code:** run `/plugin install vibecode --marketplace vibecode/vibecode`, then `/mcp` and select **vibecode** to sign in.
   - **Gemini CLI:** run `gemini extensions install https://github.com/vibecode/vibecode`, then `/mcp auth vibecode` inside Gemini CLI.
   - **The skill alone**, for any agent that reads skills: `npx skills add vibecode/vibecode`. It needs the Vibecode MCP server connected too.
2. Sign in to Vibecode (or create an account with Google or Apple) and allow access.
3. Ask for an app, for example: "Build me an iPhone app to log how much water I drink each day."

Every app you build lives in your Vibecode account, so you can keep working on it in Vibecode on the web or in the Vibecode iPhone app.

### What you can ask for

- **Build and change apps:** describe a new app, or ask for a new screen, a different color or a fix in one you've built. The chat waits for the build and tells you when it's ready.
- **Follow the agent:** see what Vibecode's agent did, why a build failed, or stop it.
- **Look inside:** read an app's logs (also its published backend's), its files and its latest screenshot, or run a command in its workspace. Keys are hidden from everything the chat sees.
- **Versions:** list an app's saved versions and bring an earlier one back. Later versions are kept.
- **Manage apps:** list, rename, duplicate or delete your apps.
- **Put it online:** deploy an app so anyone can use it, give a web app its `vibecode.run` address or connect your own domain, and password-protect it. Deploying never starts a charge from the chat: when it would cost more than your plan includes, you get a link to deploy in Vibecode.
- **Keep going elsewhere:** get links to open an app in Vibecode, on your iPhone, or to publish it to the App Store.

### Plans and credits

Creating an account and connecting is free, and a new account's first app build is free. After that, builds and changes use Vibecode credits, which you manage on [vibecodeapp.com](https://www.vibecodeapp.com). Nothing is sold in the chat.

### What's in the plugin

- `.cursor-plugin/plugin.json`: the Grok Bot plugin's manifest.
- `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json`: the Claude Code plugin and the marketplace that lists it.
- `gemini-extension.json`: the Gemini CLI extension.
- `server.json`: the Vibecode server's entry in the [MCP Registry](https://registry.modelcontextprotocol.io).
- `mcp.json`: the Vibecode server, `https://api.vibecodeapp.com/mcp`. Sign-in uses OAuth with your Vibecode account; no keys are stored in the plugin.
- `skills/vibecode`: how to use the tools well. Every plugin above includes it.

## Bugs and feature requests

Open an issue on the [Issues tab](https://github.com/vibecode/vibecode/issues) for bugs or feature requests, and react to the ones you'd like us to prioritize.

## Links

- Website: https://www.vibecodeapp.com
- Docs: https://www.vibecodeapp.com/docs
- Privacy policy: https://www.vibecodeapp.com/privacy
- Terms: https://www.vibecodeapp.com/terms
- Support: support@vibecodeapp.com

## License

The plugin is MIT licensed. See [LICENSE](LICENSE).
