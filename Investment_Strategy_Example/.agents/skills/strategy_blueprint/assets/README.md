# Assets

| File | Purpose |
|------|---------|
| `kaxanuk_logo_full.png` | Full horizontal KaxaNuk logo with tagline. Used on the cover page only. |
| `kaxanuk_mark_header.png` | Square KaxaNuk mark (orange ring on white). Used in the top-right of every page after the cover. |

If either PNG is missing, regenerate it from the canonical PDF using:

```bash
python - <<'PY'
import fitz, os
doc = fitz.open('examples/Strategy_Blueprint_Example.pdf')
out_dir = 'assets'
os.makedirs(out_dir, exist_ok=True)
xref = doc[0].get_images(full=True)[0][0]
pix = fitz.Pixmap(doc, xref)
(pix if pix.n - pix.alpha < 4 else fitz.Pixmap(fitz.csRGB, pix)).save(f'{out_dir}/kaxanuk_logo_full.png')
xref = doc[1].get_images(full=True)[0][0]
pix = fitz.Pixmap(doc, xref)
(pix if pix.n - pix.alpha < 4 else fitz.Pixmap(fitz.csRGB, pix)).save(f'{out_dir}/kaxanuk_mark_header.png')
PY
```
