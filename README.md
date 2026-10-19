# Engineering Software & Library Matrix

Browse and compare engineering software and libraries by capability and application area. The English interface is the default; use the language switch in the upper-right corner to switch to Chinese.

![Wide engineering software matrix with a left-side software details panel](assets/preview.svg)

## Features

- Compare software across Geometry, Meshing, Material Model, Load Model, Analysis Solver, and Results Analysis.
- View capability scores as bars while keeping 1–10 numeric scores in JSON.
- Select a software row to open its details to the left of the matrix on wide screens.
- Switch between capability and industry views; filter by category or license type.
- Open the **Add software** survey to prepare a prefilled GitHub issue for review.
- The issue draft includes software details, license, description, and all six scores. Review and submit it on GitHub; update `data/software.json` only after checking the submission.
- Switch the interface, metric definitions, software descriptions, and use cases between English and Chinese.

The catalog is stored in [`data/software.json`](data/software.json). `index.html` also embeds a copy for direct `file://` use. The website prepares an issue draft; it does not change the catalog automatically.

> The preview is a static layout illustration. Software logos use website favicons when available and fall back to initials.
