php-complexify
===============

PHP port of Dan Palmer's [jquery.complexify.js](https://github.com/danpalmer/jquery.complexify.js/)

## Installation

```bash
composer require mcrumley/php-complexify
```

## Usage
```php
$check = new \Complexify\Complexify();
$result = $check->evaluateSecurity('correct horse battery staple');

echo round($result->complexity, 1) . '% ';
if ($result->valid) {
    echo 'VALID';
} else {
    echo 'NOT VALID: '.implode(', ', $result->errors);
}
```

## Configuration

You can override the default configuration by passing an array to the constructor.

```php
$check = new \Complexify\Complexify(array(
    'minimumChars' => 8,          // the minimum acceptable password length
    'strengthScaleFactor' => 1,   // scale the required password strength (higher numbers require a more complex password)
    'bannedPasswords' => array(), // override the default banned password list
    'banMode' => 'strict',        // strict == don't allow substrings of banned passwords, loose == only ban exact matches
    'encoding' => 'UTF-8',        // password string encoding
));
```

## Return value

The `evaluateSecurity` method returns an object containing the following properties:

- valid - `TRUE` if the password passes all checks
- complexity - The calculated complexity as a percent of the maximum (25 characters with at least one from each set)
- errors - Zero or more strings explaining the checks that did not pass
  - banned
  - tooshort
  - toosimple

## License

This code is distributed under the WTFPL v2 licence.

## Version History

**0.4** - Changed banmode option to banMode

**0.3.1** - Added composer support

**0.3** - First release (matched version number of the JS version)
