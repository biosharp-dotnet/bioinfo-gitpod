# cowpy

**NOTE**: There is no `tldr` page for `cowpy` yet, therefore we will rely upon the traditional sources i.e. `cowpy --help` command.

### Quick introduction

`cowpy` is a program that generates ASCII (128 simplest characters with alphabets, numbers and special symbols) art pictures of a `cow` with a message. It can also generate pictures using pre-made images of other animals, such as `bunny`, `ghostbusters`, `tux` (the Linux penguin) etc.

For example,

```
# Using the default cow character    <== COMMENT IN SHELL

$ cowpy "Hello, world!"
 _______________
< Hello, world! >
 ---------------
     \   ^__^
      \  (oo)\_______
         (__)\       )\/\
           ||----w |
           ||     ||

```


### Installation

To install `cowpy` you have to use the language-level package manager for Python called `pip`.

```
pip install cowpy
```

### Exercises

#### 1. Choose a different character using the `-c` option

**TIP:** : You can use the `cowpy --list` to see which characters are available.

<details>
<summary> Solution </summary>

```bash
$ cowpy -c tux "Hello, world!" 
```

</details>

<br/>

#### 2. Use the pipe operator to provide the input phrase.


**TIP**: You can use the `echo` command to print something to screen (via `stdout`).

**TIP**: You can use the `|` (pipe) operator in `bash` to _connect_ two commands.

<details>
<summary> Solution </summary>

```bash
$ echo "Hello, world!" | cowpy
```

</details>


<br/>



#### 3. Save the output to a file.

**TIP**: You can use the `>` (redirection) operator in `bash` to send the output of a command to a file.

<details>
<summary> Solution </summary>

```bash

$ cowpy "Hello, world!" > cowpy.out.txt


# OR  You can combine all the above commands


$ echo "Hello, world!" | cowpy > cowpy.out.txt

```

</details>


<br/>


#### 4. Print the output of the saved file to screen


**TIP**: You can use the `cat` command.


<details>
<summary> Solution </summary>

```bash
$ cat cowpy.out.txt
```

</details>


<br/>




#### 5. Create a file `hello_world.txt` and add "Hello, world!" to the it.


**TIP**: It can be done using a text editor (Gitpod/nano) or it can be done using purely the command line.


<details>
<summary> Solution </summary>

```bash
$ echo "Hello, world!" > hello_world.txt
```

</details>


<br/>




#### 6. Send the contents of the `hello_world.txt` as an input to `cowsay` and save the results to a file.


**TIP**: You can use the pipe and redirection operator.


<details>
<summary> Solution </summary>

```bash
$ cat hello_world.txt | cowpy > cowpy.out.txt
```

</details>


<br/>




#### 7. Remove the files which you created.


**TIP**: You can use the `rm` command to achieve this.


<details>
<summary> Solution </summary>

```bash
$ rm cowpy.out.txt hello_world.txt
```

</details>


<br/>


### CONGRATULATION on concluding an adventure with Linux tools, scripting and `cowpy`!
