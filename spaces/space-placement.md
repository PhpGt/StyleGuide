# Space placement

## No extra space should be placed after a control structure keyword or function name

[Please see the PHP docs for a list of all control structure keywords][control-structures].

Good example:

```php
require("file.php");

function goodExample() {
	while(true) {
		if(true) {
			break;
		}
	}

	return;
}
```

Bad example:

```php
require ("file.php");

function badExample () {
	while (true) {
		if (true) {
			break;
		}
	}

	return ;
}
```

## Opening brackets should not have a space after, closing brackets should not hace a space before

Good example:

```php
function goodExample(int $number, string $word) {
	if($number == $word) {
		for($i = 0; $i < $number; $i++) {
			doSomething($word);
		}
	}
}
```

Bad example:

```php
function badExample( int $number, string $word ) {
	if( $number == $word ) {
		for( $i = 0; $i < $number; $i++) {
			doSomething( $word );
		}
	}
}
```

## Commas separating variable lists should have a space or newline after, no whitespace before

Variable lists include function parameters and array contents.

Good example:

```php
function goodExample(int $number, string $word, bool $truth):array {
	$defaultArray = [$number, $word];

	return array_merge($defaultArray, [
		$truth,
		123,
		456,
	]);
}
```

Bad example:

```php
function badExample(int $number , string $word , bool $truth):array {
	$defaultArray = [$number , $word];

	return array_merge($defaultArray, [
		$truth ,
		123    ,
		456    ,
	]);
}
```

## A space should surround binary and ternary, but not unary operators

Unary operators take one value, such as the logical not operator, `!`.

Binary operators take two values, such as the addition operator, `+`.

Ternary operators take three values. In PHP there is only one ternary operator, `? :` and is often referred to as the ternary operator.

Good example:

```php
$continue = !$stop;
$five = 2 + 3;
$action = empty($_POST["action"]) ? "default" : $_POST["action"];
$action = $_POST["action"] ?? "default";
```

Bad example:

```php
$continue = ! $stop;
$five = 2+3;
$action = empty($_POST["action"])?"default":$_POST["action"];
$action = $_POST["action"]??"default";
```

## A space should surround all type operators

[String, array and type operators][operators] should always be surrounded by a single space, so it is clear that they are affecting the variable on the left side. This includes **concatenation**, **pushing** and **instance checking**.

Most importantly, the array push operator should be surrounded by spaces so that it is not confused with an array assignment operator. `$a []= 1` has a totally different meaning to `$a[0] = 1`.

Good example:

```php
$array = []; // Assignment operator, surrounded by spaces.
$array []= "Hello"; // Push operator, surrounded by spaces.
$array[0] .= "World"; // Concatenation operator, surrounded by spaces.
```

Bad example:

```php
$array= []; // Assignment operator is not surrounded both sides by a space.
$array[] = "Hello"; // Push operator is disguised as an assignment operator.
$array [0]. = "World"; // Confusing spaces - what is happening here?
```

[control-structures]: http://php.net/manual/language.control-structures.php
[operators]: http://php.net/manual/en/language.operators.php
