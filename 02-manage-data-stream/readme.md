## Data streams

### Standard input - 0

- **default standard input is keyboard**
- **not all commands accept standard input, eg: wc, cat, grep**
- **wc (with no arguments) → waits for input from keyboard**
  - Enter wc command it will give to enter text - so this is the standard input
- **wc logs → reads from the file logs.**
- **wc < logs → redirects the file logs into stdin**

---

- **`wc logs`**: The program directly opens the file `logs` (does not use standard input)
- **`wc < logs`**: The shell opens the file and connects it to standard input (file descriptor 0), then `wc` reads from standard input

<img src="./image1.png">

> To you as a user, both commands appear to produce the same result, but internally they work slightly differently.

In the Linux world, **Standard Input (stdin)** is the data stream that goes into a command. While we usually type this data via the keyboard, Linux offers several powerful ways to automate or redirect that flow.

Think of it like a plumbing system: you can source your "water" (data) from a faucet, a tank, or even the output of another pipe.

---

### 1. Using Pipes (`|`)

The pipe is the most common way to provide input. It takes the **Standard Output** of one command and feeds it directly into the **Standard Input** of another.

- **Syntax:** `command1 | command2`
- **Example:** `cat names.txt | sort`
  - _What happens:_ The list of names is sent into the `sort` command as its input.

### 2. Input Redirection (`<`)

If you have data saved in a file and want a command to read that file as if you were typing it into the terminal, use the `<` operator.

- **Syntax:** `command < file.txt`
- **Example:** `wc -l < log.txt`
  - _What happens:_ The `wc` (word count) command receives the contents of `log.txt` as stdin.

### 3. "Here Documents" (`<<`)

A **Heredoc** allows you to type multiple lines of input directly into the terminal or a script until a specific "delimiter" word is reached. This is great for multi-line strings or configuration blocks.

- **Example:**

  ```bash
  cat << EOF
  This is line 1.
  This is line 2.
  EOF
  ```

  - _What happens:_ Everything between the two `EOF` tags is sent to `cat`.

### 4. "Here Strings" (`<<<`)

If you just want to pass a simple string or a variable as input without creating a file or using `echo`, use the triple chevron.

- **Syntax:** `command <<< "string"`
- **Example:** `base64 <<< "password123"`
  - _What happens:_ The string "password123" is fed directly into the base64 encoder.

---

#### Quick Comparison Table

| Method         | Operator | Best Use Case                                     |
| :------------- | :------- | :------------------------------------------------ |
| **Pipe**       | `\|`     | Passing data from one tool to another in a chain. |
| **Redirect**   | `<`      | Using an existing file as input.                  |
| **Heredoc**    | `<<`     | Providing multi-line text blocks in scripts.      |
| **Herestring** | `<<<`    | Passing a single string or variable.              |

## Standard output - 1

- **default standard output is terminal**
- **du Images 1> output.txt**

## Standard error - 2

- **default standard error is terminal**
- **du Images 2> output.txt**

### Redirect Both standard output and error

- **du Images &> output.txt**
- **du Images 1> output.txt 2> error.txt**

### /dev/null

- **apt install wget -y 1> /dev/null**
- **apt install wget -y 1> /dev/null 2> /tmp/error.txt**

### Command > output 2>&1 vs Command 2>&1 > output

- **du Images > output.txt 2>&1**
  - First redirect stdout to output.txt
  - Then redirect stderr to the same location as stdout

- **du Images 2>&1 > output.txt** (Redirects stderr to stdout, then stdout to output.txt)
  - First redirect stderr to stdout location (which means to the terminal)
  - Then redirect stdout to output.txt

---

## Pipes

<img src="pipes.png" width=600>

### std error will not be piped to the next command

- **du Images | wc -l** (This will only count the lines of stdout, not stderr)
- **du Images 2>&1 | wc -l** (This will count the lines of both stdout and stderr)
