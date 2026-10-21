# Vibecode

[Vibecode](https://www.vibecodeapp.com) builds iPhone apps and web apps from a description. Vibecode's agent writes the app, builds it and tests it.

This repository holds the Vibecode plugin for Grok Bot, and it's where you can report Vibecode bugs and request features.

## The Vibecode plugin

Build and change apps by chatting. From the chat you can follow a build, ask for changes, and look inside an app when something isn't working.

### Getting started

1. Install the Vibecode plugin and select **Connect**.
2. Sign in to Vibecode (or create an account with Google or Apple) and allow access.
3. Ask for an app, for example: "Build me an iPhone app to log how much water I drink each day."

Every app you build lives in your Vibecode account, so you can keep working on it in Vibecode on the web or in the Vibecode iPhone app.

### What you can ask for

- **Build and change apps:** describe a new app, or ask for a new screen, a different color or a fix in one you've built. The chat waits for the build and tells you when it's ready.
- **Follow the agent:** see what Vibecode's agent did, why a build failed, or stop it.
- **Look inside:** read an app's logs (also its published backend's), its files and its latest screenshot, or run a command in its workspace. Keys are hidden from everything the chat sees.
- **Versions:** list an app's saved versions and bring an earlier one back. Later versions are kept.
- **Manage apps:** list, rename, duplicate or delete your apps.
- **Keep going elsewhere:** get links to open an app in Vibecode, on your iPhone, or to publish it to the App Store.

### Plans and credits

Creating an account and connecting is free, and a new account's first app build is free. After that, builds and changes use Vibecode credits, which you manage on [vibecodeapp.com](https://www.vibecodeapp.com). Nothing is sold in the chat.

### What's in the plugin

- `.cursor-plugin/plugin.json`: the plugin's manifest.
- `mcp.json`: the Vibecode server, `https://api.vibecodeapp.com/mcp`. Sign-in uses OAuth with your Vibecode account; no keys are stored in the plugin.
- `skills/vibecode`: how to use the tools well.

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
