# Standards

## All files must only use `UTF-8`, without `BOM`

Throughout all code and across all servers, UTF-8 should be used to avoid any ambiguities when dealing with paths, browsers and other areas of HTTP that are only UTF-8 compatible.

Therefore, actual PHP source files should only use UTF-8 encoding, and should not start with the Byte Order Marking characters.

The Unicode Standard neither requires nor recommends the use of the BOM for UTF-8, but does allow the character to be at the start of a file. The presence of the UTF-8 BOM may cause problems with existing software that could otherwise handle UTF-8.

All good code editors can be configured to use different file encodings.

## Always use UTC timezone to store date and time

For consistency and to avoid ambiguity with timezones and daylight saving, all dates and times should be stored in UTC. All servers and databases can also be set to work in UTC, and that way the dates and times within your software will always be normalised, allowing the developer to set the default timezone per-application or per-user, where appropriate.

The use of `DateTime` objects and timestamps should be seen as interchangeable depending on use case. Unix timestamps are limited to UTC, so storing DateTime objects in anything other than UTC can cause confusion when translating between the two.