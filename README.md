php-complexify
===============

PHP port of Dan Palmer's [jquery.complexify.js](https://github.com/danpalmer/jquery.complexify.js/)

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
