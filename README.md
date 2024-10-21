# Betty Style Configuration for Nano

https://github.com/hs-hq/Betty

https://github.com/alx-tools/Betty/wiki

https://github.com/alx-tools/Betty/wiki/Tools:-Emacs

https://github.com/alx-tools/Betty/wiki/Tools:-Vim

https://github.com/alx-tools/Betty/wiki/Tools:-Atom


Here for custom nano with `Betty linter`

This guide provides steps to configure the `nano` text editor to follow the Betty coding style guide, especially for C programming.

To configure the `nano text editor` to adhere to the Betty style guide, `especially for C code`, you can set up syntax highlighting, enable tab to space conversion, and ensure proper indentation rules.

Here’s how to set up nano to comply with the Betty coding style/doc:

## Requirements

- `nano` text editor
- `Betty style/doc checker` (optional but recommended for Ubuntu 22.04)

## Step 1: Open/Create Nano Configuration File

To configure `nano`, you need to edit the `\.nanorc` file in your home directory:

```bash
nano ~/.nanorc
```

If the file does not exist, this command will create it.

## Step 2: Add Betty-Compliant Configuration

Add the following code to `\.nanorc` to enforce the Betty style:

```bash
## Set tab size to 8 spaces
set tabsize 8

## Set  8 spaces size to tab
## set tabgives "        "

## Convert tabs to spaces automatically
set tabstospaces

## Enable auto-indentation
set autoindent

## Highlight syntax for C files
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

## Enable line numbering
set linenumbers

## Display column position
set const

## limit 80 column
set fill 80
```

## Step 3: Save the Configuration

After adding the above lines to `.nanorc`, save the file by pressing:

1. `Ctrl + X`
2. Then `Y` to confirm
3. Press `Enter` to exit

## Step 4: Using Nano

Now, every time you edit C code in `nano`, the editor will:

- Follow the `Betty-compliant` indentation rules (tab size = 8, convert tabs to spaces).
- `Highlight C keywords`, types, strings, and numbers.
- `Show line numbers` and `current column positions` to help adhere to the `80-character limit`.

### Explanation of the configuration:

- set tabsize 8: Sets the tab size to 8 spaces, as required by Betty.
- set tabstospaces: Ensures that all tabs are converted into spaces.
- set autoindent: Automatically indents new lines, following the current indentation.
- syntax highlighting: The syntax "c" "\.c$" block provides basic syntax highlighting for C code, including keywords, types, comments, strings, and numbers.
- set linenumbers: Enables line numbers on the left, which can help with identifying lines that exceed the limit.
- set const: Shows the current column position, helpful to keep track of the 80-character limit.

## Step 5: Use Nano with the Configuration

Now, whenever you open a C file in nano, the editor will follow Betty's indentation and syntax highlighting rules, and convert tabs to spaces, ensuring that your code style is compliant with Betty.

## Step 6: Install Betty Style/Doc Checker in Ubuntu 22.04

To automate the process of checking if your code follows the Betty style, you can install the `betty` tool:

1. Clone the Betty repository:

```bash
git clone https://github.com/hs-hq/Betty
git clone https://github.com/holbertonschool/Betty.git
```

2. Install the `Betty style/doc checker` with:

Set up Betty with a symbolic link
```bash
chmod a+x install.sh
sudo ./install.sh
```

3. Use the following commands to check your files:

Once installed, you can check your files by running:
```bash
betty <filename.c>
```

## Conclusion

This configuration ensures that `nano` will format your C code according to the Betty style guide. Additionally, the `Betty checker tool` can help automate the process of verifying code style and doc compliance.
EOL



## More Info BETTY LINTER for UBUNTU 22.04:
`Betty linter`
To run the Betty linter just with command `betty <filename>`:

Go to the `Betty repository`
`Clone` the repo to your local machine
cd into the Betty directory
`Install the linter` with sudo `./install.sh`
emacs or vi or nano a new file called `betty`, and `copy the script below`:
```bash
#!/bin/bash
# Simply a wrapper script to keep you from having to use betty-style
# and betty-doc separately on every item.
# Originally by Tim Britton (@wintermanc3r), multiargument added by
# Larry Madeo (@hillmonkey)

BIN_PATH="/usr/local/bin"
BETTY_STYLE="betty-style"
BETTY_DOC="betty-doc"

if [ "$#" = "0" ]; then
    echo "No arguments passed."
    exit 1
fi

for argument in "$@" ; do
    echo -e "\n========== $argument =========="
    ${BIN_PATH}/${BETTY_STYLE} "$argument"
    ${BIN_PATH}/${BETTY_DOC} "$argument"
done
```

Once saved, exit file and `change permissions` to apply to all users with `chmod a+x betty`
Move the betty file into `/bin/ directory` or somewhere else in your `$PATH with sudo mv betty /bin/`
You can now type betty <filename> to run the `Betty linter`!



## Exportation extension VSCode
Comment exporter la liste des extensions vscode sur un autre PC?

Pour exporter la liste des extensions installées sur Visual Studio Code et les réinstaller sur un autre PC, voici comment procéder :

### Exporter les extensions

1.Ouvrir le terminal de VS Code sur l’ordinateur d’origine.

2.Exécutez la commande suivante pour lister toutes les extensions installées et les enregistrer dans un fichier texte :

```bash
code --list-extensions > extensions-list.txt
```
Cette commande crée un fichier nommé `extensions-list.txt` dans le répertoire actuel contenant les noms de toutes les extensions installées.

3.Copiez le fichier `extensions-list.txt` sur votre nouvel ordinateur (par exemple, via un service cloud ou une clé USB).

### Importer les extensions

1.Ouvrir le terminal de VS Code sur le nouvel ordinateur.

2.Exécutez la commande suivante pour installer toutes les extensions listées dans le fichier :
```bash
cat extensions-list.txt | xargs -n 1 code --install-extension
```
Cette commande lira chaque ligne du fichier et installera l'extension correspondante.

Avec ces étapes, vous pouvez facilement transférer toutes vos extensions VS Code d'un ordinateur à un autre.
