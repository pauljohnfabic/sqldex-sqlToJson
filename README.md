# SQLDEX — sqlToJson

A Pokédex-themed, pixel-art converter between **SQL Server results and JSON**, in both directions.
It's a single `index.html` with no build step and no dependencies. Your data never leaves the browser.

**Try it live: https://pauljohnfabic.github.io/sqldex-sqlToJson/**

## SQL → JSON

In SSMS, select your results in the grid → right-click → **Copy with Headers** (`Ctrl`+`Shift`+`C`) and paste.

- Reads SSMS grid copies, "Results to Text" output, CSV, semicolon- and pipe-separated text, and Excel copies, with auto-detection
- Outputs an array of objects, an object keyed by the first column, columns + rows, or JSON Lines
- Detects numbers, booleans, `NULL` and ISO dates; values with leading zeros (zip codes, account numbers) and numbers too large for JavaScript stay strings
- Can rename keys to camelCase, snake_case or lowercase

## JSON → SQL

Paste a JSON array of objects, JSON Lines, or a single object.

- Generates batched `INSERT` statements (1000 rows per batch), one `INSERT` per row, or `UPDATE` statements keyed on the first column
- Optional `CREATE TABLE` with inferred types: `INT` / `BIGINT`, `DECIMAL(p,s)`, `BIT`, `DATE`, `DATETIME2`, `DATETIMEOFFSET`, `NVARCHAR(n)`
- Nested objects and arrays are stored as JSON text in `NVARCHAR(MAX)`
- Options for table name, column naming (as-is, PascalCase, snake_case), Unicode `N'…'` literals, a wrapping transaction, and `IDENTITY_INSERT`

## Usage

Use the live page above, or download `index.html` and open it in any modern browser. The pixel fonts load from Google Fonts; without a connection the page falls back to a monospace font and still works.

## License

[MIT](LICENSE) © 2026 Paul John Fabic
