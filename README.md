# RepoSsessed

RepoSsessed is a project designed to parse public source code repositories and find various types of vulnerabilities. Here are some of the methods I'm looking at including.

- Coding flaws that lead to critical vulnerabilities
- Hardcoded passwords
- Sensitive configuration files
- Database connection strings
- Private SSL keys
- Private SSH keys
- Uploaded Unix/Linux home directories, with sensitive dotfiles
- <code>~/.ssh</code> directories full of keys
- Source code of projects you're currently doing blackbox testing on
- Etc...

## Philosophy

Finding flaws in public source code repositories is not a new idea, and many have done great work in the area.

The reason this project was created was twofold:

1. To add **source code flaws** to the public source code repository conversation. So, not just looking for information disclosure, but actual coding flaws as well, e.g., input validation mistakes that can lead to critical bugs in various languages. 
2. I am looking to **collapse all useful code repository signatures, including my own for coding flaws, into a single, flat, transparent format that can be used by ANY engine**. This way you can write whatever interface you'd like and use the evergreen signatures from this project.
3. Due to regular issues with leveraging search APIs, e.g., limiting sensitive (dangerous) searches and rate limiting, **this project works by searching the repo locally** post-clone.

## Current implementation

Currently the tool works in two ways:

1. Searches within a repo for a number of sensitive files.
2. Searches within a repo for a number of sensitive strings within files.

## Usage

There are two primary ways to use this project.

1. Create your own tool and use the <code>filetypes.txt</code> and <code>strings.txt</code> files as your search content.
2. Use the provided scripts to perform the actual searches.

If you're doing #2, simply clone this repo, <code>cd</code> into it, drop the repo you want to test into the <code>./target</code> directory, and then run the <code>./repossessed.sh</code> script, which will create your results in <code>results.txt</code>.

## Credits

I'd like to give credit to the following people for either their prior work or their contributions:

- Samar Dhwoj Acharya for allowing me to use signatures from his Github Dorks project
- Michael Henriksen for allowing me to use signature files from his GitRob project

### Notes

1. If you benefit from this project and think of any other signatures, please submit them to the project through pull requests or issues. The project will always remain open and transparent so that people can benefit from the shared signatures, and it's always nice to keep that going.
