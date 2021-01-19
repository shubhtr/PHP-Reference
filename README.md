# PHP Reference

## Variables and Constants

### Defining Variables

### Types of Data

### Variable Scope

### Predefined Variables

### Variable-handling Functions

### Constants

    define(name, value, true/false)

#### Default PHP constants

Constant                | Description
---                     | ---
`__LINE__`              | denotes the number of the current line in a file
`__FILE__`              | is the full path and filename of the file
`__DIR__`               | directory of the file
`__FUNCTION__`          | name of the function
`__CLASS__`             | class name, includes the namespace it was declared in
`__TRAIT__`             | the trait name, also includes the namespace
`__METHOD__`            | the class method name
`__NAMESPACE__`         | name of the current namespace

## array

## return

## namespace

## require_once

## dirname(__FILE__)

## use

## function

## throw - try - catch - Exception

## class/objects

### class

    <?php
    class Fruit {
        //properties
        public $name;
        public $color;

        //methods
        function set_name($name) {
            $this->name = $name;
        }
        function get_name() {
            return $this->name;
        }
    }
    ?>

<ins>Note</ins>: In a class, variables are called properties and functions are called methods.

### object

Objects of a class are created using the `new` keyword. Each object has all the properties and methods defined in the class, but they will have different property values.

    <?php
    class Fruit {
        //properties
        public $name;
        public $color;

        //methods
        function set_name($name){
            $this->name = $name;
        }
        function get_name(){
            return $this->name;
        }
        function set_color($color) {
            $this->color = $color;
        }
        function get_color(){
            return $this->color;
        }
    }

    $apple = new Fruit();
    $banana = new Fruit();

    $apple->set_name('apple');
    $apple->set_color('red');

    $banana->set_name('banana');

    echo $apple->get_name();
    echo "<br>";
    echo $apple->get_color();
    echo "<br>";
    echo $banana->get_name();
    ?>

### $this

`$this` keyword refers to the current object, and is only available inside methods.

### private
### public


## File Operations

### fopen
<ins>Description:</ins> open a file

    <?php
        $myfile = fopen("dictionary.txt", "r") or die("Unable to open file!");
        echo fread($myfile, filesize("dictionary.txt"));
        fclose($myfile);
    ?>

Modes | Description
--- | ---
r | <b>Open a file for read only.</b> File pointer starts at the beginning of the file
w | <b>Open a file for write only.</b> Erases the contents of the file or creates a new file if it doesn't exist. File pointer starts at the beginning of the file
a | <b>Open file for write only.</b> The existing data in file is preserved. File pointer starts at the end of the file. Creates a new file if the file doesn't exist.
x | <b>Creates a new file for write only.</b> Returns FALSE and an error if file already exists
r+ | <b>Open a file for read/write.</b> File pointer starts at the beginning of the file .
w+ | <b>Open a file for read/write.</b> Erases the contents of the file or creates a new file it it doesn't exist. File pointer starts at the beginning of the file. 
a+ | <b>Open a file for read/write.</b> The existing data in file is preserved. File pointer starts at the end of the file. Creates a new file if the file doesn't exist.
x+ | <b>Creates a new file for read/write.</b> Returns FALSE and an error if file already exists. 

### fread
<ins>Description:</ins> read from a file

    fread($myfile, filesize("dictionary.txt"));

### fclose
<ins>Description:</ins> close an open file

    <?php
        $myfile = fopen("dictionary.txt", "r");
        //some code to be executed...
        fclose($myfile);
    ?>

## References
* https://www.w3schools.com/php/
