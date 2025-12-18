# BCON Syntax Highlighting for VS Code

<img src="icon.png" alt="BCON" width="200"/>

Syntax highlighting extension for BCON (BCON Configures Only Nicely) configuration language.

## Features

- ✨ Full syntax highlighting for `.bcon` files
- 🎨 Support for all BCON language features:
  - Keywords: `import`, `use`, `as`, `from`, `export`, `skip`
  - Comments: single-line (`#`) and multi-line (`'...'`)
  - String interpolation with `[Main.property]` and `[This.property]`
  - Data types: strings, numbers, BigInt, booleans, dates, regex, files
  - Special constants: `True`, `False`, `Null`, `Undefined`, `NaN`, `Infinity`
  - Array (`@*`) and dictionary (`@key`) syntax
  - Destructuring and imports
- 📝 Proper tokenization for semantic highlighting

## Get BCON Parser

https://github.com/parrotcore/bcon-parser

## Installation

Install from VS Code Marketplace or search for "BCON Syntax highlighting" in VS Code extensions.

## Recommended Extensions

For enhanced productivity when working with BCON files, we recommend:

- **[Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)** - Autocompletes file paths in import statements

### Setup Path Intellisense for BCON

After installing Path Intellisense, it should work automatically in strings. If you want to customize it, add to your VS Code settings (`Ctrl+,` → Open Settings JSON):

```json
{
  "path-intellisense.mappings": {
    "./": "${workspaceRoot}"
  },
  "path-intellisense.extensionOnImport": true,
  "path-intellisense.autoSlashAfterDirectory": true
}
```

Then when typing:
```bcon
import "./
```
You'll see file and folder suggestions.

## Example

```bcon
# Single line comment
'Multi-line comment'

import [cityType] from "./cityTypes.bcon".utf8;

use "production" as environment;
use 8080 as port;

export [
    @environment => environment;
    @port => port;
    @greeting => "Welcome to [Main.environment]!";
];
```

## License

MIT

## Links

- **BCON Parser:** [github.com/parrotcore/bcon-parser](https://github.com/parrotcore/bcon-parser)
- **npm:** [npmjs.com/package/bcon-parser](https://www.npmjs.com/package/bcon-parser)
