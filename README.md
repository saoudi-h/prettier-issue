# Steps to Reproduce the Issue with Prettier

This document explains the steps you have taken so far in an attempt to reproduce an issue encountered with Prettier when dealing with files with special names.

## Step 1: Creating the Test Project

1. Using `npx create-next-app@latest` to create a Next.js project.
2. Selecting configuration options such as TypeScript, Tailwind CSS, and ESLint.
```bash
√ Would you like to use TypeScript? ... No / Yes
√ Would you like to use ESLint? ... No / Yes
√ Would you like to use Tailwind CSS? ... No / Yes
√ Would you like to use `src/` directory? ... No / Yes
√ Would you like to use App Router? (recommended) ... No / Yes
√ Would you like to customize the default import alias? ... No / Yes
√ What import alias would you like configured? ... @/*
```

## Step 2: Installing Prettier

1. Installing Prettier as a development dependency: 

```pwsh
    npm install -D prettier
```

## Step 3: Creating a Test File

1. Creating the file `.src/pages/api/auth/[...nextauth].ts`.
2. Adding simple TypeScript code to the test file.

## Step 4: Attempting to Run Prettier

1. Trying to run Prettier on the test file using the command: `npx prettier --write "./src/pages/api/auth/[...nextauth].ts"`.
2. Receiving the error: `[error] Explicitly specified file was ignored due to negative glob patterns: "./src/pages/api/auth/[...nextauth].ts".`.

## Step 5: Attempting to Escape Special Characters

1. Attempting to escape special characters in the file name `[...nextauth].ts` using different methods, including the caret ("^","`","\") character in PowerShell.
2. No escape method succeeded in resolving the issue under Windows.

## Step 6: Testing with Zsh Terminal

1. Running the same command with a Zsh terminal: `npx prettier --write ./src/pages/api/auth/\[...nextauth\].ts`.
2. The command successfully works in Zsh after escaping the brackets.

## Step 7: Testing with Custom Command

1. Adding a custom command to the `package.json` file: `"format:fix": "prettier --write --ignore-path .gitignore ."`
2. The `npm run format:fix` command successfully formats all target files, including `[...nextauth].ts`.

## Step 8: Conclusion

Unfortunately, the issue persists under Windows, even after multiple attempts to escape special characters in the `[...nextauth].ts` file name. Prettier continues to reject the file due to negative glob patterns.


## My setup

generated with: 

```pwsh
npx envinfo --system --binaries --npmPackages --markdown "next,react,prettier,typescript"
```
### System:
 - OS: Windows 10 10.0.22621
 - CPU: (16) x64 AMD Ryzen 7 5800X 8-Core Processor
 - Memory: 8.16 GB / 31.93 GB
### Binaries:
 - Node: 18.15.0 - C:\Program Files\nodejs\node.EXE
 - Yarn: 1.22.19 - C:\Program Files\nodejs\yarn.CMD
 - npm: 9.8.1 - C:\Program Files\nodejs\npm.CMD
 - pnpm: 8.6.12 - C:\Program Files\nodejs\pnpm.CMD
### npmPackages:
 - @types/node: 20.6.2 => 20.6.2
 - @types/react: 18.2.21 => 18.2.21
 - @types/react-dom: 18.2.7 => 18.2.7
 - autoprefixer: 10.4.15 => 10.4.15
 - eslint: 8.49.0 => 8.49.0
 - eslint-config-next: 13.4.19 => 13.4.19
 - next: 13.4.19 => 13.4.19
 - postcss: 8.4.29 => 8.4.29
 - prettier: ^3.0.3 => 3.0.3
 - react: 18.2.0 => 18.2.0
 - react-dom: 18.2.0 => 18.2.0
 - tailwindcss: 3.3.3 => 3.3.3
 - typescript: 5.2.2 => 5.2.2

 ### additional informations

(does not work on Windows with these terminals)

- PowerShell: Version 7.3.6
- cmd
- Git Bash

It worked on 
- Ubuntu WSL (Zsh terminal).