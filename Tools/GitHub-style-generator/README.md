# GitHub Style Generator

This tool generates the GitHub style (`MacDown/Resources/Styles/GitHub-2020.css`)
from the official GitHub style package, using [Dart Sass](https://sass-lang.com/dart-sass).

The generated stylesheet is committed to the repository, so you do **not** need
Node.js to build MacDown. To regenerate or update the style, run:

```bash
npm ci
npm update primer-markdown
make
```
