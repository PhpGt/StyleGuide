# Standards.

## All files must only use `UTF-8`, without `BOM`.

Throughout all code and across all servers, UTF-8 should be used to avoid any ambiguities when dealing with paths, browsers and other areas of HTTP that are only UTF-8 compatible.

Therefore, actual PHP source files should only use UTF-8 encoding, and should not start with the Byte Order Marking characters.

The Unicode Standard neither requires nor recommends the use of the BOM for UTF-8, but does allow the character to be at the start of a file. The presence of the UTF-8 BOM may cause problems with existing software that could otherwise handle UTF-8.

All good code editors can be configured to use different file encodings.

## Always use UTC timezone to work with date and time.

// TODO.
