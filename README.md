# Samples of OOP & FP in PHP 8

## Object-Oriented Programming in PHP 8

- Class-related Keywords
  - `class`, `interface`, `abstract class`, `trait`
- Visibility Keywords
  - `public`, `protected`, `private`
- Inheritance and Implementation
  - `extends`, `implements`
- Constructor and Destructor
  - `__construct()`, `__destruct()`
- `readonly` Keyword
  - `readonly`
- `final` Keyword
  - `final`
- `static` Keywords
  - `static` 
- class Constants  
- `const` 


### Abstract Classes

Abstract classes are declared with the abstract keyword and are used to define methods that must be implemented by any subclass that extends the abstract class.

```php
<?php
abstract class DatabaseDriver
{
    private $host;
    private $db;
    private $uid;
    private $password;
    public function __construct($host, $db, $uid, $password)
    {
        $this->host     = $host;
        $this->db       = $db;
        $this->uid      = $uid;
        $this->password = $password;
    }
}

```

### Interfaces

An interface in PHP is used to define a set of methods that implementing classes must adhere to. Interfaces are similar to abstract classes in that they cannot be instantiated and any class that implements an interface must implement all of its methods. However, interfaces cannot have properties or full method implementations, while abstract classes can.

```php
<?php

interface Database
{
    public function db_connect();
    public function add($data);
    public function get($where);
    public function update($where);
    public function remove($where);
}
```

### Classes and Inheritance

```php
<?php

class MySQLDriver extends DatabaseDriver implements Database {

    public function __construct($host, $db, $uid, $password) 
    { 
        parent::__construct($host, $db, $uid, $password); 
    }

    public function db_connect() 
    {

    }
    
    public function remove($where) 
    { 

    } 
    
    public function add($data) 
    { 

    } 

    public function get($where) { 
    
    } 
    
    public function update($where) {
        
    } 
} 

```

### Traits 

Traits are a mechanism for code reuse in single inheritance languages such as PHP. A Trait is intended to reduce some limitations of single inheritance by enabling a developer to reuse sets of methods freely in several independent classes living in different class hierarchies. The semantics of the combination of Traits and classes is defined in a way which reduces complexity, and avoids the typical problems associated with multiple inheritance and Mixins.

A Trait is similar to a class, but only intended to group functionality in a fine-grained and consistent way. It is not possible to instantiate a Trait on its own. It is an addition to traditional inheritance and enables horizontal composition of behavior; that is, the application of class members without requiring inheritance.

```php
<?php
trait Hello {
    public function sayHello() {
        echo 'Hello ';
    }
}

trait World {
    public function sayWorld() {
        echo 'World';
    }
}

class MyHelloWorld {
    use Hello, World;
    public function sayExclamationMark() {
        echo '!';
    }
}

$o = new MyHelloWorld();
$o->sayHello();
$o->sayWorld();
$o->sayExclamationMark();

// Output:
// Hello World!
```

## Functional Programming in PHP 8