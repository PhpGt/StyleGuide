# PHP tags

## The first line of all `.php` files should be exactly "`<?php`"

When PHP parses a file, it looks for opening and closing tags, `<?php` and `?>` which tell PHP to start and stop interpreting the code between them. Any characters outside of these tags will be served as text by the webserver.

A common mistake to make is having a newline or other whitespace character preceding the opening PHP tag. This will cause the character to be sent to the output buffer, in turn causing the HTTP headers to be sent before the execution of the script.

This will cause unwanted side effects or fatal errors if the script requires the use of sessions or cookies.

Good example:

```php
<?php
session_start();
echo "Stored name:" . $_SESSION["name"];
```

Bad example:

```php

 <?php
session_start(); // fatal error here!
echo "Stored name:" . $_SESSION["name"];
```

## Never use the closing PHP tag (`?>`)

If a file is pure PHP code, it is preferable to omit the PHP closing tag at the end of the file. This prevents accidental whitespace or new lines being added after the PHP closing tag, which may cause unwanted effects because PHP will start output buffering when there is no intention from the programmer to send any output at that point in the script.

Typically, the [DOM](https://github.com/phpgt/dom) will be used for manipulating page content, so there is no reason to be closing PHP tags at all midway through the file.

## Never use PHP short tags

The PHP parser can also be set to look for a short opening tag style, `<?`, but this is discouraged as it is only available if the current PHP interpreter is configured to do so. The main reason programmers use the short tags is to allow a shorthand for `<?php echo "example"; ?>` as `<?="example"?>` when outputting content inline within HTML, but as PHP.Gt applications shouldn't be used in this way, there is no benefit of using short tags.