# Utility Scripts

This repo is a collection of useful scripts for tools like terminals, code formatting/linting, etc.

*More Details To Be Added*


## Tested & Supported Platforms

1. MacOS

*These scripts have not been tested nor validated in a Windows environment and would likely need modifications to ensure compatibility.*


## Terminal
1. `terminal/shared/.function-go`
    - Enables the terminal to quickly navigate the user to their github repo (or any additional sites added by the user)
    - Example:
        - Github:
            ```bash
                goto git --repo 'repo_name'
            ```
2. `terminal/shared/.terminal-shortcuts`
    - Adds various helpful shortcuts to the terminal:
        ```bash
            alias add="git add --all"
            alias ac="git add --all && git commit -m"
            alias commit="git commit -m"
            alias dev="cd desktop/dev"
            alias gbd="git branch -D"
            alias gbl="git branch --list"
            alias gc="git checkout -b"
            alias gdc="git diff --cached"
            alias master="git checkout master && git pull origin master"
            alias main="git checkout main && git pull origin main"
            alias status="git status"
        ```
    - As well as a shorthand to push changes to the remote branch:
        ```bash
            gpob() {
                # Check if we are in a Git repository
                git rev-parse --is-inside-work-tree &>/dev/null || {
                    echo "Not inside a Git repository."
                    return 1
                }

                # Get current branch name
                local branch

                branch=$(git symbolic-ref --short HEAD 2>/dev/null)
                
                if [[ -z "$branch" ]]; then
                    echo "Could not determine the current branch."
                    return 1
                fi

                # Push to origin
                echo "Pushing to origin $branch..."
                
                git push origin "$branch"
            }
        ```
    
    Together, the `gpob()` function and shortcuts can be used to streamline your git interactions.

    Example:
    1. add and commit local branch changes
        ```bash
        ac "commit message"
        ```
    2. push branch changes to repo
        ```bash
        gpob
        ```
3. `terminal/.zshrc`
    - Example script showing how to implement for your given terminal instance
