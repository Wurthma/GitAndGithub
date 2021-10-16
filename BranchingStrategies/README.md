# Branching Strategies, Conflicts, and Pull Requests

## Merging commits and cherry-pick

When we have multiple commits, we can merge them with the command:

`git rebase -i HEAD~3`

The above command will merge the last 3 commits.

After that, a screen will be displayed where we should 'squash' the commits and 'pick' the commit we want to keep.

Finally, we can write a message and use `:x` to save.

`git cherry-pick 2efd26a` will only bring the changes from commit 2efd26a to the current branch.

## Finding changes in commits

We can use `git bisect start` to navigate between commits and find a specific change.

After the execution of **bisect start** we need to inform the initial and final commit where we will search:

1- `git bisect bad HEAD` -> HEAD to get the current commit from the branch or we can use a specific commit
2- `git bisect good c2a801e` -> final commit that will limit the search.

Git will navigate between commits, and you can use `git bisect bad` to report that it hasn't found the changes you're looking for yet, and `git bisect good` to report that the change has already been found.

`git bisect reset` will end the search.

Or to find responsible:

`git blame <fileName>` shows us who is responsible for each line in the file.

## Gitflow

![Gitflow example](./resources/git-flow-example_1.png)

![Gitflow example](./resources/git-flow-example_2.png)

## Tools

Below are some tools that can help with versioning with Git:

- GitKraken
- GitHub Desktop
- Glue Git
