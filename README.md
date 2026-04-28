# ModBuilder ((Neo)Forge)

> A GitHub Actions-powered build pipeline for packaging Minecraft Forge mods — no local toolchain required.

---

## What is ModBuilder?

ModBuilder lets you compile and package your Minecraft Forge mod entirely through GitHub. Just upload your source, trigger the workflow, and download a ready-to-use `.zip` containing both the main jar and sources jar.

### Versions supported
Forge
- 1.20.1
- 1.8.9

NeoForge
- 1.20.1 (untested)
---

## Prerequisites

- A GitHub account
- A copy of this repository made from the template
- Your mod source files as a `.zip`

---

## Usage

Follow these steps every time you want to build your mod:

### 1. Use the Repository Template

Click **Use this template** at the top-right of this page to create your own copy.

### 2. Upload Your Mod's Zip

Upload your mod's `.zip` file and the workflow will take care of the rest. Your zip can be structured in one of two ways:

**Option A** — files at the root of the zip:
```
your-mod.zip
├── build.gradle
├── gradle.properties
└── src/
    └── ...
```

**Option B** — files inside a `mod/` folder:
```
your-mod.zip
└── mod/
    ├── build.gradle
    ├── gradle.properties
    └── src/
        └── ...
```

### 3. Choose the Right Workflow

Each workflow in the **Actions** tab corresponds to a specific version of Minecraft Forge. Make sure you select the workflow that matches your mod's target version — running the wrong one may produce an incompatible build.

### 4. Trigger the Build Workflow

1. Go to the **Actions** tab of your repository.
2. Select **Build Workflow** from the list on the left.
3. Click **Run workflow**.
4. Select your target branch from the dropdown.
5. Click the green **Run workflow** button.

### 5. Download Your Build

Once the workflow completes (usually a minute or two), navigate to the finished run. Under **Artifacts**, you'll find a `.zip` containing:

- `mod-<version>.jar` — the main mod jar
- `mod-<version>-sources.jar` — the sources jar

---

## File Structure Expectations

```
your-mod.zip
├── build.gradle
├── gradle.properties
└── src/
    └── main/
        ├── java/
        └── resources/
            └── META-INF/
                └── mods.toml
```

> Make sure your zip follows standard Forge mod project conventions or the build may fail.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Workflow doesn't appear | Check that Actions are enabled in your repository settings |
| Build fails immediately | Check that your zip structure matches one of the two supported formats |
| Wrong mod version built | Double-check you selected the correct workflow for your Forge version |
| Artifacts missing after run | The workflow may have failed — check the logs for errors |
| Mod not loading in game | Ensure `META-INF/mods.toml` is present and correctly formatted |

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## License

[GNU General Public License v3.0](LICENSE)
