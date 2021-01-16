# PHP Reference

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
