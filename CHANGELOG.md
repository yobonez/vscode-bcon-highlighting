# Changelog

## v2.1.0 - 2025-12-21

### New Features - BCON 2.2.0 Support
- **Class System Support** 🎉
  - Added syntax highlighting for `class` keyword
  - Added support for `extends` keyword (class inheritance)
  - Added support for `includes` keyword (composition - reserved for future)
  - Highlighting for class names in PascalCase (e.g., `City`, `Address`)
  - Type annotations with `:` operator
  - Optional fields with `?` operator
  - Default values with `=` operator in class fields
  
- **Type System Support**
  - Primitive types: `String`, `Number`, `Boolean`, `BigInt`, `Date`, `RegExp`, `Array`, `Object`, `Any`
  - Custom class types recognized as references (e.g., `Coordinates`, `Address`)
  - Type annotations in field definitions highlighted correctly
  - Nested object and array types support

### Examples
```bcon
# Class definition
class City [
    @name: String;
    @population: Number;
    @founded?: Date;
];

# Class with inheritance
class CapitalCity extends City [
    @parliament: String;
    @isCapital: Boolean = True;
];

# Creating class instances
use City [
    @name => "Warsaw";
    @population => 1720000;
] as warsaw;
```

### Improvements
- Better tokenization for class-related syntax
- Enhanced type reference highlighting
- Improved context-aware field definition highlighting

### New Snippets
- `class` - Basic class definition
- `classext` - Class with inheritance
- `field` - Required class field
- `fieldopt` - Optional class field
- `fielddef` - Field with default value
- `useclass` - Create class instance

## v2.0.0 - 2025-12-18

### Major Improvements
- **Complete rewrite** of syntax highlighting to support BCON 2.0
- Added support for `export` keyword (required in BCON 2.0)
- Added support for `from` keyword (destructuring and imports)
- Added support for `skip` keyword (array destructuring)
- Fixed multi-line comments to use single apostrophes `'...'` (not `'''`)
- Improved string interpolation highlighting with `[Main.property]` and `[This.property]`
- Enhanced support for all BCON data types:
  - Numbers: decimal, hex (`0xFF`), binary (`0b1010`), octal (`0o755`), BigInt (`123n`)
  - Special values: `True`, `False`, `Null`, `Undefined`, `NaN`, `Infinity`
  - Regular expressions with flags: `/pattern/flags`
  - Dates: `"DD-MM-YYYY, HH:MM:SS.MS".date`
  - File references with encoding: `"./file.txt".utf8`
- Better tokenization for variables, properties, and references
- Fixed accessor dot highlighting (was misspelled as "puntuation")
- Improved context-aware highlighting for different sections
- **Fixed comment highlighting after semicolons and other non-string contexts**

### New Features
- **Code snippets** - Added 15+ snippets for common BCON patterns (import, use, export, etc.)
- **Language reference** - Complete BCON language documentation in Polish
- **Better auto-closing** - Improved bracket and quote auto-closing behavior
- **Path Intellisense support** - Documentation for file path autocompletion

### Breaking Changes
- Multi-line comments now use `'...'` instead of `'''...'`' (matches BCON spec)
- Removed incorrect multi-line string pattern (standard strings can be multi-line)

## v1.0.1
- Added missing "This" keyword
