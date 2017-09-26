# Path mapping

## Directories and files must either be namespace-mapped or web-mapped.

The pathnames throughout a project must be obvious by either mapping directly to a class's namespace, or relate to a requested URL.

### Namespace-mapping example

Assuming a project's root directory is at `/app`, and the namespace root for `MyApp` is set to `./src/class`:

`/app/src/class/User/Settings.php`:

```php
<?php
namepsace MyApp\User;

class Settings {
// ...
}
```

### Web-mapping example

If a PHP class acts as a controller for page logic its pathname must correspond to the requested URL it serves. Hyphens in URLs must be mapped to underscores in filepaths.

A consistent set of rules must be used. Assuming a project's root directory is at `/app`, the base page directory is set to `./page`, and the class suffix for pages is `_Page`:

URL requested `http://example.com/user/settings`

`/app/src/page/user/settings.php`:

```php
<?php
namespace MyApp\Page\User;

class Settings_Page {
// ...
}
```

URL requested: `http://example.com/post-list`

`/app/src/page/post_list.php`:

```php
<?php
namespace MyApp\Page;

class Post_List_Page {
// ...
}
```

## Namespaces must map to file paths, as per PSR-4.

A PHP class pathname must correspond to its fully qualified class name with respect to PSR-4 namespace root(s) defined in the project.

`composer.json`

```json
{
	"autoload": {
		"psr-4": {
			"MyApp\\": "src/class"
		}
	}
}
```

`/app/src/class/Model/User.php`:

```php
<?php
namespace MyApp\Model;

class User {
// ...
}
```