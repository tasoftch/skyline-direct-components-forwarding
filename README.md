# Skyline Component Forwarding
This package allows you to register directories as direct accessable component sources.

#### Installation
```bin
$ composer require skyline/direct-components-forwarding
```

#### Usage
With this package, another Component class is available.

Just use it in your component.config.php file:

```php
<?php
use Skyline\Component\Config\OpenDirectoryComponent;

return [
    // Can be any name. Including it into template has no effect.
    'Open' => new OpenDirectoryComponent(
        '/Library',     // URI prefix  => <img src="/Public/Library/my-image.jpg">
        __DIR__ . "/path/to/library"
    )
];
```

This example will look for a file at:
````__DIR__ . "/path/to/library/my-image.jpg````  
If it finds one, its gonna be delivered, otherwise a 404 error is given (except other plugins are able to resolve the request into a existing component.)

Please note that the URIs and paths are recursive:  
````html
<img src="/Public/Library/media/users/me.jpg" />
````
will be resolved to
````php
<?php
__DIR__ . "/path/to/library/media/users/me.jpg";
````