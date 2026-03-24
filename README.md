# rars-web

Embeds the RARS RISC-V Assembler & Runtime Simulator into a browser using [CheerpJ](https://cheerpj.com/), allowing students to run RARS without installing Java.

Built for CPRE 3810 at Iowa State University.

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

GitHub will build and publish the site. The URL will be:
```
https://tyler-bibus.github.io/rars-web/
```

> **Note:** The `.nojekyll` file in this repo tells GitHub Pages to skip Jekyll processing, which is required so the `.jar` file is served correctly.

### 2. Verify It Works

Visit the URL above. You should see a loading spinner followed by the RARS GUI rendering in the browser window. Initial load takes 10–30 seconds as CheerpJ downloads the JVM runtime.

---

## Embedding in Canvas (Iowa State)

Canvas allows embedding external tools and URLs via the **Rich Content Editor**.

### Option A — iframe Embed (Recommended)

In a Canvas page or assignment description:

1. Open the Rich Content Editor
2. Click **Insert** → **Embed**  
   *(or switch to HTML source view with the `</>` button)*
3. Paste the following iframe, replacing the URL with your GitHub Pages URL:

```html
<iframe
  src="https://tyler-bibus.github.io/rars-web/"
  width="100%"
  height="700"
  style="border: 1px solid #ccc; border-radius: 4px;"
  allow="cross-origin-isolated"
  title="RARS RISC-V Simulator">
</iframe>
```

> **Canvas Note:** Iowa State's Canvas instance may restrict iframes to whitelisted domains. If the embed is blocked, use Option B.

### Option B — External Tool Link

If iframes are restricted, link directly to the GitHub Pages URL as an **External URL** assignment or module item:

1. In your Canvas module, click **+** → **External URL**
2. Paste: `https://tyler-bibus.github.io/rars-web/`
3. Check **Load in a new tab** (recommended for full-screen RARS experience)
4. Name it: *RARS RISC-V Simulator*

### Option C — LTI / New Quizzes (Advanced)

For tighter integration (auto-grading, etc.), an LTI tool configuration can wrap the GitHub Pages URL. Contact your Canvas admin if needed.

---

## Local Development

To test locally without GitHub Pages, you need a local server (browsers block JAR loading from `file://`):

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
| `RARS_CPRE3810.jar` | Customized RARS build for CPRE 3810 |
| `.nojekyll` | Disables Jekyll on GitHub Pages (required for JAR serving) |

---

## License

RARS is open source under the MIT License. See the [RARS GitHub repo](https://github.com/TheThirdOne/rars) for details.
