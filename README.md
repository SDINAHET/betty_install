# Betty Style Configuration for Nano


https://github.com/alx-tools/Betty/wiki

https://github.com/alx-tools/Betty/wiki/Tools:-Emacs

https://github.com/alx-tools/Betty/wiki/Tools:-Vim

https://github.com/alx-tools/Betty/wiki/Tools:-Atom


Here for custom nano with Betty linter

This guide provides steps to configure the \`nano\` text editor to follow the Betty coding style guide, especially for C programming.

## Requirements

- \`nano\` text editor
- Betty style checker (optional but recommended)

## Step 1: Open/Create Nano Configuration File

To configure \`nano\`, you need to edit the \`.nanorc\` file in your home directory:

```bash
nano ~/.nanorc
```

If the file does not exist, this command will create it.

## Step 2: Add Betty-Compliant Configuration

Add the following code to \`.nanorc\` to enforce the Betty style:

```bash
## Set tab size to 8 spaces
set tabsize 8

## Convert tabs to spaces automatically
set tabstospaces

## Enable auto-indentation
set autoindent
```

## Highlight syntax for C files
```bash
syntax "c" "\\.c$"
color green "\\<(if|else|for|while|return|switch|case|default)\\>"
color blue "\\<(int|char|float|double|void|long|short|signed|
unsigned|static|const|struct|union|enum)\\>"
color cyan "\\<(printf|scanf|fopen|fclose|malloc|free|sizeof|memcpy|memset)\\>"
color brightyellow "\\<(NULL|true|false)\\>"
color red "\\/\\*.*\\*\\/"  ## comments /* */
color red start="\\/\\*" end="\\*\\/"  ## multi-line comments
color red "//.*$"  ## comments starting with //
color brightmagenta ""[^\"]*""  ## strings
color brightblue "-?[0-9]+(\\.[0-9]+)?([eE][-+]?[0-9]+)?([fFlLuU]?)"  ## numbers
```

## Enable line numbering
```bash
set linenumbers
```

## Display column position
```bash
set const
```

## Step 3: Save the Configuration

After adding the lines, save the file by pressing:

1. \`Ctrl + X\`
2. Then \`Y\` to confirm
3. Press \`Enter\` to exit

## Step 4: Using Nano

Now, every time you edit C code in \`nano\`, the editor will:

- Follow the Betty-compliant indentation rules (tab size = 8, convert tabs to spaces).
- Highlight C keywords, types, strings, and numbers.
- Show line numbers and current column positions to help adhere to the 80-character limit.

## Optional: Install Betty Style Checker

To automate the process of checking if your code follows the Betty style, you can install the \`betty\` tool:

1. Clone the Betty repository:

```bash
git clone https://github.com/holbertonschool/Betty.git
```

2. Install the Betty style checker with:

```bash
sudo ./install.sh
```

3. Use the following commands to check your files:

```bash
betty <filename.c>
```

## Conclusion

This configuration ensures that \`nano\` will format your C code according to the Betty style guide. Additionally, the Betty checker tool can help automate the process of verifying code style compliance.
EOL
