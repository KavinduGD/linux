# Shell Expansions

> Before command executing, the shell "rewrites" and parses the command

## Filename Expansion

- Also known as Globbing.

- ls \* - Bash replaces \* with all files in the current directory
- ls \*.txt - Bash replaces \*.txt with all files that end with .txt

## Tilde Expansion

- ~ - Expanded in to environment variable $HOME

## Variable Expansion

- $HOME - Expanded to the value of the environment variable HOME
- 🛑 Basically if we use a $ with a variable, bash replace it with the value of the variable.

> echo $HOME

- In here we not referencing the string "$HOME", expanding the value of the variable HOME
- To reference a variable in bash , we use like this. **Home=/root**

#### php vs bash variable expansion

```bash
var="world"
echo "Hello $var"
```

```php
$var = "world";
echo "Hello $var";
```

- In php echo $var mean reference the variable $var
- In bash echo $var mean expand the value of the variable var

### useful variable expansions

- **${VAR:-default}** - If VAR is set and not null, expand to its value, otherwise expand to default.
- **${#VAR}** - Expand to the length of the value of VAR.
- **${VAR:offset:length}** - Expand to the substring of VAR starting at offset with the specified length.
- **{VAR/pattern/replacement}** - Replace the first occurrence of pattern in VAR

## Word Splitting

- **After variable expansion, bash splits the result into words**
- **Word splitting is done based on the characters in the IFS variable**
- Character in IFS - **space, tab, newline**

  > touch file1 file2
  - This command will splitted in to 3 words - touch, file1, file2
  - First word is the command, and the rest are arguments to the command

### Expansion ---->> Word Splitting

## " Double Quotes " and Word Splitting

- **😀 " " - Prevents word splitting** (How ever ~ expansion, \* expansion and many expansion are not supported . **Variable expansion works**)

> touch "a b"

- This command has 2 words - touch, a b
- So create a file named "a b"

> touch a b

- This command has 3 words - touch, a, b
- So create 2 files named "a" and "b"

## ' Single Quotes ' and Word Splitting

- **😀 ' ' - Prevents word splitting and all expansion (including variable expansion)**

```BASH
file_name=a

touch '$file_name b'
```

- This command has 2 words - touch, $file_name b
- So create a file named "$file_name b"

### 💯 the Quotes ( " " , ' ' ) only define how the expansion and splitting are done. Nothing to do with String like other programming languages

## Escape Character \

- **😀 \ - Prevents the special meaning of the next character**

> touch a\ b

- This command has 2 words - touch, a b
- So create a file named "a b"

- **cannot use inside single quotes** because single quotes prevent the special meaning of all characters inside it.

## Brace Expansion

- **😀 { } - expand string of characters**

> touch file{1..3}.txt

- This command has 4 words - touch, file1.txt, file2.txt, file3.txt

## Command Substitution

- **😀 $(command) - treat the output of command as a string**
- **😀 `command` - treat the output of command as a string** (old style, not recommended)

> echo "Today is $(date)"

## Process Substitution

- **😀 <(command) - treat the output of command as a file**

> diff <(ls dir1) <(ls dir2)

- ls dir1 outputs the filenames in dir1.
- ls dir2 outputs the filenames in dir2.
- diff compares the two “files” which are actually the outputs of the two ls commands.

- **😀 >(command) - treat the input to command as a file**

> echo Hello > >(cat)

- echo Hello writes Hello\n into its stdout.
- That stdout is redirected to /dev/fd/63.
- /dev/fd/63 is a pipe to cat.
