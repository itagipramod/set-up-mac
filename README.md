# Setting Up Your Mac for Development

This guide will walk you through setting up your Mac for software development. Whether you're a beginner or an experienced developer, these steps will help you get your environment ready for coding.

## Step 1: Install Xcode Command Line Tools

We don't need to install Xcode as we are not developing any Apple based applications. Instead we need Command Line Tools. This is required to run commands in Terminal. It's just a package which contains most of the commands.

To install Xcode Command Line Tools, just run the below code in Terminal.

Open Terminal and run the below command.

```bash
xcode-select --install
```

## Step 2: Install Homebrew

Homebrew is a popular package manager for macOS that makes it easy to install and manage software packages. To install Homebrew, open Terminal and run the following command.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions to complete the installation.

## Step 3: Install Git

Git is a version control system used by many developers. You can install Git using Homebrew. In Terminal, run the below command.

```bash
brew install git
```

Verify the installation by checking the Git version.

```bash
git --version
```

We need to git setup username and email to keep track of the user who commits/saves the changes in Github.

To setup username and email in Git, run the following commands once the git is installed and verified.

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
```

## Step 4: Install Node.js

If you're working with JavaScript or TypeScript, you'll need Node.js and npm (Node Package Manager). Install Node.js using Homebrew or directly you can install using [Download NodeJS](https://nodejs.org/en/download) and follow on screen instructions.

```bash
brew install node
```

Verify the installation using below commands:

```bash
node --version
npm --version
```

## Step 5: Install Yarn

Yarn is the package manager to install JavaScript dependencies. We can use yarn to add, remove, update or configure the packages in our project.

First, you need to install Yarn using homebrew package manager. Use below command.

```bash
brew install yarn
```

Verify the installation using below command:

```bash
yarn --version
```

## Step 6: Install MySQL

MySQL is an open-source relational database management system (RDBMS) essential for running MySQL queries and managing databases. To streamline the process, we use MySQL Workbench, a user-friendly UI application that allows for direct query execution and database management.

Installing MySQL is crucial for our development environment since many of our applications rely on it. MySQL is widely used in the industry and offers compatibility with most deployment tools, making it a reliable choice for our projects.

To install MySQL, we are using homebrew. Run below commands.

```bash
brew search mysql
brew install mysql@5.7  
```

Once installation is complete, just run below commands in terminal.

```bash
echo 'export PATH="/opt/homebrew/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc
export LDFLAGS="-L/opt/homebrew/opt/mysql@5.7/lib"  
export CPPFLAGS="-I/opt/homebrew/opt/mysql@5.7/include"
brew services start mysql@5.7
```

After this, close and reopen the terminal. To verify MySQL version, run below command.

```bash
mysql --version
```

After this, to start command line MySQL, run below command.

```bash
mysql -uroot 
```

## Step 7: Install MySQL Workbench

After installing MySQL, it's essential to install MySQL Workbench. It is a GUI based application which can be used to run the queries, view tables, export data and many more actions through GUI.

Writing queries manually in terminal sometimes becomes difficult task as queries will be not be saved. We can use MySQL Workbench to perform all these and it's very easy to use as well.

To install MySQL Workbench, just run below command.

```bash
brew install --cask mysqlworkbench
```

Once the installation gets successful, open the MySQL Workbench application and set up database name, port, user and password etc.

## Step 8: Install Visual Studio Code

Visual Studio Code (VS Code) is a popular code editor developed by Microsoft. It's lightweight, extensible, and great for web development. Download and install VS Code from the official website: [Visual Studio Code](https://code.visualstudio.com/) or install it using Homebrew using below command.

```bash
brew install --cask visual-studio-code
```

Follow on screen instructions and complete the installation.

Once the installation is complete, run the below command to verify if VS Code is installed properly and can be accessible through command line.

```bash
code .
```

## Step 9: Show branch name and present working directory in Terminal

Sometimes we might need to know on which branch we are working upon and what is the current directory where we are committing the changes.

Every time running the command like git branch or pwd is an unnecessary task.

To simplify this, copy and paste the below code in.zshrc or .bashrc file and save it.

Open the .zshrc file using below command.

```bash
code ~/.zshrc
```

and paste the following code.

```bash
parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}
COLOR_DEF='%f'
COLOR_USR='%F{243}'
COLOR_DIR='%F{197}'
COLOR_GIT='%F{39}'

NEWLINE=$'\n'

setopt PROMPT_SUBST
export PROMPT='${COLOR_USR}%n@%M ${COLOR_DIR}%d ${COLOR_GIT}$(parse_git_branch)${COLOR_DEF}${NEWLINE}%% '
```

Once the code is saved in the file, just simply restart the Terminal. Voila! branch name and current directory will be visible in Terminal.

## Additional Resources

- [Official Xcode Documentation](https://developer.apple.com/xcode/)
- [Homebrew Documentation](https://docs.brew.sh/)
- [Git Documentation](https://git-scm.com/doc)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Yarn Documentation](https://classic.yarnpkg.com/lang/en/docs/)
- [MySQL Workbench Documentation](https://dev.mysql.com/doc/)
- [Visual Studio Code Documentation](https://code.visualstudio.com/docs)

---
