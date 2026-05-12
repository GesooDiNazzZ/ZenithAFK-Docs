# Installation

## Download

Download ZenithAFK from [BuiltByBit](https://builtbybit.com/resources/zenithafk.107444/).

## Requirements

| Requirement | Version |
|---|---|
| Server software | Paper 1.20+ (or Folia) |
| Java | 21 or newer |
| PlaceholderAPI | Optional (soft dependency) |
| Vault + Economy plugin | Optional (auto-detected) |

## Steps

1. **Stop your server** before installing.
2. Place `ZenithAFK-1.0.0.jar` in your `plugins/` folder.
3. **Start the server** — ZenithAFK will generate default config files on first run.
4. Edit `plugins/ZenithAFK/config.yml` to your liking (or use the in-game GUI editor).
5. Run `/zafk reload` to apply changes.

## License

The license is injected automatically when downloading from BuiltByBit. If you obtained the plugin elsewhere, open a ticket on [Discord](https://discord.com/invite/MbY3FM3Evk) to request your license key.

## Vault Economy (Optional)

If Vault and an economy plugin (e.g., EssentialsX, CMI Economy) are installed, ZenithAFK automatically detects them. No configuration needed — just add `money: 500` to any reward and it will be deposited to the player's balance.

## PlaceholderAPI (Optional)

Install [PlaceholderAPI](https://modrinth.com/plugin/placeholderapi) to use ZenithAFK placeholders in chat, TAB, scoreboards, and any plugin that supports PAPI. No additional expansion needed — ZenithAFK registers its own placeholders automatically.