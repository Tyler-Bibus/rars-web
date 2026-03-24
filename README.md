# rars-web

Embeds the RARS RISC-V Assembler & Runtime Simulator into a browser using [CheerpJ](https://cheerpj.com/), allowing people to run RARS without installing Java.

---

## How It Works

`index.html` loads CheerpJ (a JVM compiled to WebAssembly) from Leaning Technologies' CDN, then runs `RARS_CPRE3810.jar` directly in the browser. No server-side Java required.


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

## Files

| File | Description |
|---|---|
| `index.html` | CheerpJ loader + RARS launcher |
| `RARS_CPRE3810.jar` | Customized RARS build |
| `.nojekyll` | Disables Jekyll on GitHub Pages (required for JAR serving) |

---

## License

RARS is open source under the MIT License. See the [RARS GitHub repo](https://github.com/TheThirdOne/rars) for details.
