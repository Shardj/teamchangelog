# Why
The conventional changelog faces many issues for larger products or teams:
- Git conflicts when adding to a standard changelog many people are working on with diverging branches.
- You manually need to edit the file and change [unreleased] to [{new release tag}] and or add to the new tag manually.

# Functionality
1. Instead of adding to your changelog directly when a ticket is in progress you should create a file named after the ticket under the changes directory, the path for which you set in the teamchangelog.yaml file.
2. Changes that need to be added to your changelog can simply be added to your newly created ticket file from the previous step.
3. When you're ready for deployment simply run the package bash file, use -v to specify the tag to add the changes under in your changelog
4. `./package -h` to see additional functionality

# Example
Example changelog in current state:
    # Tag: 14.4.0	Packaged on: Wed 24 Apr 10:16:03 BST 2019
    TM-85 - fixed a bug
	
And you have the change "foo bar" under ticket file "TM-86" in your changes directory. Running `./package -v 14.4.1` results in that ticket file being deleted and your changelog looking like:
    # Tag: 14.4.1	Packaged on: Wed 24 Apr 12:35:10 BST 2019
    TM-86 - foo bar
	
    # Tag: 14.4.0	Packaged on: Wed 24 Apr 10:16:03 BST 2019
    TM-85 - fixed a bug
	
# Missing functionality
If you have any suggestions or changes feel free to open issues or PR's.

Currently this is written in bash because for my usecase it was easy and means not having to add additional libraries or packages to build servers and dockerfiles. Something like Python compiled to C may be the best future option for ease of development and usage, feel free to raise issues over this with suggestions.

Future functionality:
Add ability to choose format of release header from yaml file settings instead of it being # Tag: {tag}	Packaged on: {date}
Ability to override yaml file options with flags/parameters when executing
