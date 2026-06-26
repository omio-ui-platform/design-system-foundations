# Dotty Font Assets

Snapshot date: 2026-05-26

Dotty typography uses GT Walsheim Pro. These licensed Omio font files are included so engineers and AI-generated local prototypes can render Dotty typography with the correct typeface before visual QA.

Source folder:
https://drive.google.com/drive/folders/1YOgXczIRZnB0V9pdBtkvZYdMef69a6mV

## Files

| File | CSS family | Weight | Style |
| --- | --- | ---: | --- |
| `GT-Walsheim-Pro-Regular.otf` | `GT Walsheim Pro` | 400 | normal |
| `GT-Walsheim-Pro-Medium.otf` | `GT Walsheim Pro` | 500 | normal |
| `GT-Walsheim-Pro-Bold.otf` | `GT Walsheim Pro` | 700 | normal |
| `GT-Walsheim-Pro-Regular-Oblique.otf` | `GT Walsheim Pro` | 400 | italic |
| `GT-Walsheim-Pro-Medium-Oblique.otf` | `GT Walsheim Pro` | 500 | italic |
| `GT-Walsheim-Pro-Bold-Oblique.otf` | `GT Walsheim Pro` | 700 | italic |

## CSS Example

Use the relative path that matches the consuming project.

```css
@font-face {
  font-family: "GT Walsheim Pro";
  src: url("./assets/fonts/GT-Walsheim-Pro-Regular.otf") format("opentype");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

Generated implementations must load GT Walsheim Pro from these assets before visual QA. If a fallback font is used because the files cannot be loaded in the target environment, report that as a QA caveat instead of treating the output as fully Dotty-compliant.
