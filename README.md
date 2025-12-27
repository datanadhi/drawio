# Draw.io Diagrams Repository

A centralized repository for managing technical diagrams and architecture documentation using [draw.io](https://www.drawio.com/).

## 🚀 Features

### Automated SVG Export
Every time you push a `.drawio` file, GitHub Actions automatically:
- Exports all diagrams to SVG format (dark theme)
- Places exported files in the `export/` directory
- Commits the changes back to the repository

### Dark Theme Support
All exported SVGs use a dark color scheme optimized for:
- Dark-themed documentation sites
- GitHub dark mode
- Modern IDEs and viewers

## 📝 Usage

### Creating/Editing Diagrams

1. **Edit online**: Open any `.drawio` file directly on GitHub
2. **Edit locally**: Use [draw.io Desktop](https://github.com/jgraph/drawio-desktop/releases) or the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio)
3. **Save and commit** your changes

### Adding New Diagrams

```bash
# Create a new diagram in the appropriate directory
touch documentation/architecture/highlevel/my-diagram.drawio

# Edit the diagram using draw.io
# Then commit and push
git add documentation/architecture/highlevel/my-diagram.drawio
git commit -m "Add my-diagram architecture"
git push
```

The workflow will automatically generate `my-diagram.svg` in the `export/` folder.

### Embedding Diagrams

Reference the auto-generated SVG files in your documentation:

```markdown
![Architecture Diagram](documentation/architecture/highlevel/export/echopost.svg)
```

## 🔧 Workflow Configuration

The automated export is configured in `.github/workflows/image-creation.yaml`:

- **Trigger**: Pushes affecting `**/*.drawio` files or manual dispatch
- **Export format**: SVG with dark theme
- **Background**: Solid (not transparent)
- **Action used**: [rlespinasse/drawio-export-action@v2](https://github.com/rlespinasse/drawio-export-action)

### Manual Trigger

You can manually trigger the export workflow:
1. Go to the **Actions** tab
2. Select "Export Drawio diagrams to SVG"
3. Click **Run workflow**

## 📚 Available Diagrams

### Architecture Documentation
- **echopost.drawio** - EchoPost system architecture
- **sdk.drawio** - SDK architecture (Initialization, Logger, Workers)

## 🛠️ Local Development

### Prerequisites
- [draw.io Desktop](https://github.com/jgraph/drawio-desktop/releases) or
- [VS Code](https://code.visualstudio.com/) with [Draw.io Integration](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio)

### Testing Export Locally (Optional)

If you want to test SVG export locally:

```bash
# Using Docker
docker run --rm -v "$PWD":/data rlespinasse/drawio-export:latest \
  --format svg \
  --theme dark \
  documentation/architecture/highlevel/your-diagram.drawio
```

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Create your diagram in the appropriate directory
2. Follow the naming convention: `lowercase-with-hyphens.drawio`
3. Commit with a clear message describing the diagram
4. The automated workflow will handle SVG generation

---

**Note**: SVG files in `export/` directories are auto-generated. Do not edit them manually as they will be overwritten.
