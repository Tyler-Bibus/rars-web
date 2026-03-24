# rars-web

Embeds the RARS RISC-V Assembler & Runtime Simulator into a browser using [CheerpJ](https://cheerpj.com/), allowing people to run RARS without installing Java.

---

## How It Works

`index.html` loads CheerpJ (a JVM compiled to WebAssembly) from Leaning Technologies' CDN, then runs `RARS_CPRE3810.jar` directly in the browser. No server-side Java required.

---

## Deploying to GitHub Pages

### 1. Enable GitHub Pages

- Go to your repo on GitHub → **Settings** → **Pages**
- Under **Source**, select **Deploy from a branch**
- Branch: `main` | Folder: `/ (root)`
- Click **Save**

GitHub will build and publish the site at:
```
https://tyler-bibus.github.io/rars-web/
```

> **Note:** The `.nojekyll` file in this repo tells GitHub Pages to skip Jekyll processing, which is required so the `.jar` file is served correctly.

### 2. Verify It Works

Visit the URL above. You should see a loading spinner followed by the RARS GUI rendering in the browser. Initial load takes 10–30 seconds as CheerpJ downloads the JVM runtime.

---

## Embedding in a Website

You can embed the simulator in any webpage using an iframe:

```html
<iframe
  src="https://tyler-bibus.github.io/rars-web/"
  width="100%"
  height="700"
  style="border: 1px solid #ccc; border-radius: 4px;"
  title="RARS RISC-V Simulator">
</iframe>
```

Alternatively, link directly to the GitHub Pages URL and open it in a new tab for a full-screen experience.

---

## Local Development

To test locally, you need a local server (browsers block JAR loading from `file://`):

```bash
cd rars-web
python3 -m http.server 8080
# then open http://localhost:8080
```

---

## Files

| File | Description |
|---|---|
| `index.html` | CheerpJ loader + RARS launcher |
| `RARS_CPRE3810.jar` | Customized RARS build |
| `.nojekyll` | Disables Jekyll on GitHub Pages (required for JAR serving) |

---

## License

RARS is open source under the MIT License. See the [RARS GitHub repo](https://github.com/TheThirdOne/rars) for details.
