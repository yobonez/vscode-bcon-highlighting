# Changelog

## v2.2.1 - 2025-12-21

### Bug Fixes
- **String Interpolation**
  - Fixed multiline interpolation support: `"text [\nvariable\n] more"` now works correctly
  - Fixed multiple interpolations in the same string
  - Added support for multiline comments `'...'` inside interpolation
  - Improved interpolation pattern to prevent empty matches that blocked parsing
  - Fixed interpolation across newlines (empty brackets with newlines now work)

### Improvements
- **Code Optimization**
  - Removed global `braces` pattern that interfered with interpolation
  - Optimized string interpolation patterns for better multiline handling
  - Added negative lookbehind `(?<!\\)` for proper escaped quote handling
  - Reduced pattern complexity for better performance

## v2.2.0 - 2025-12-21

### New Features - BCON 2.3.0 Support
- **Constructor Parameters** 🎉
  - Added syntax highlighting for class constructor parameters: `class Name (param1, param2)`
  - Support for spread operator in constructor parameters: `class Station (name, ...lines)`
  - Parameter names highlighted with proper scopes
  
- **Constructor Calls**
  - Full support for constructor calls: `use ClassName(arg1, arg2)`
  - Nested constructor calls: `District("Name", Coordinates(55.7, 37.6))`
  - Arguments highlighting (strings, numbers, variables, nested constructors)
  
- **Nullish Coalescing Operator**
  - Added support for `?` operator in default values: `value ? default`
  - Proper highlighting in class fields and expressions
  
- **Spread Operator**
  - Support for spread syntax: `...array`, `...object`
  - Spread in arrays: `[...arr1; ...arr2]`
  - Spread in constructor arguments: `ClassName(...args)`
  
- **Enhanced Operators**
  - Changed default value operator from `=` to `=>`
  - Empty array literals `[]` properly handled
  - Array type annotations: `@lines: [String]`

- **Bracket Support**
  - Added auto-closing pairs for parentheses `()`
  - Bracket matching for round brackets
  - Proper nesting support

### Bug Fixes
- Fixed issue where empty arrays `[]` in default values caused next line parsing errors
- Fixed array type pattern order to prevent incorrect matching
- Fixed optional field type highlighting with `?` operator
- Improved pattern specificity for class field values

### Improvements
- Enhanced variable recognition after spread operator
- Better export statement highlighting with variable names
- Improved constructor argument parsing with nested calls
- More robust pattern matching for edge cases

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
