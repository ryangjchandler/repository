# 📦 Repository

This package provides a stupidly simple class that can be extended to create simple repository classes in your Laravel applications.

## Installation

You can install this package via Composer:

```bash
composer require ryangjchandler/repository
```

## Usage

To create a new repository, extend the base `Repository` class and specify which model should be targeted.

```php
<?php

namespace App\Repositories;

use App\User;
use RyanChandler\Repository\Repository;

class UserRepository extends Repository
{
    protected $model = User::class;
}
```

And there you go. You can now use the "Repository pattern" in your applications.

### Adding methods

Any calls to non-existent methods on your repository will be delegated to the model class.

```php
<?php

namespace App\Repositories;

use App\User;
use RyanChandler\Repository\Repository;

class UserRepository extends Repository
{
    protected $model = User::class;

    public function findByEmail(string $email)
    {
        return $this->where('email', $email)->first();
    }
}
```

Calling `$this->where()` is the same as calling `Model::where()`.