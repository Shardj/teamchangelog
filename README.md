# Why
The conventional changelog faces many issues for larger products or teams:
- Git conflicts when adding to a standard changelog many people are working on, especially common with diverging branches being used.
- You manually need to edit the file and change `[unreleased]` to `[{new release tag}]` and or add to the new tag manually.

# Functionality
### Basic usage
1. Instead of adding to your changelog directly when a ticket is in progress you should create a file named after the ticket under the changes directory. The path for your changes directory and your changelog should be set in your package.conf file.
2. Changes that need to be added to your changelog can simply be added to your newly created ticket file from the previous step.
3. When you're ready for deployment simply run the package bash file, use -v to specify the tag to add the changes under in your changelog.
4. Your changelog file will now have the new tag with the changes you wrote to ticket files.
5. `./package -h` to see additional functionality.

### Notable functionality you may trip up on
- Hidden files (beginning with .) in the changes directory will be ignored.
- Paths in the conf file are absolute if starting with / otherwise they're relative to the directory the conf file is kept in.
- The conf file must be in the same directory as the bash file.
- This repo no longer automatically creates a git tag, it just handles the movement of files under changes/ to changelog

# Example
I have included an example changelog, example changes directory, and example unreleased change (in the changes directory). If you clone this repo and run `teamchangelog/package -v 1.0` you'll be able to clearly see what's happening from `git diff` and `git status`.

# Missing functionality
If you have any suggestions or changes feel free to open issues or PR's.

Currently this is written in bash because for my usecase it was easy and means not having to add additional libraries or packages to build servers and dockerfiles. Something like Python compiled to C may be the best future option for ease of development and usage, feel free to raise issues over this with suggestions.
