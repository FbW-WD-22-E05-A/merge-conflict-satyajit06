# Context

Git and GitHub were designed to help people to work together on a coding project. It makes it easy for each member of the the team to download the entire code base for the project to their local development computer and work on specific parts of the project.

Each member can share their proposed changes with the whole team for the others to test. When the project leader is happy with a given change, or when a consensus about it is reached among all members of the team, the proposed change can be added (merged) to the main code base. Each team member can then synchronize their local copy of the project with the newly-updated main code base, and continue working on their specific features.

This exercise imagines that you are working in a very small team, with a project leader (owner) and a team member. Here's how such a project would typically work.

## Repositories
1. The owner creates a repository on GitHub to act as the "source of truth" for the project (**the owner's Github repository**).
2. Only the owner has admin rights to this repository.
3. Team members will be able to read from this repository and copy from it, but will not be able to write to it.
4. The owner will make a clone of this repository on their local development computer, in order to contribute changes (**the owner's local clone**).
5. The team members will make a _fork_ of the owner's repository on GitHub (**the team member's GitHub fork**).
6. Each team member will have admin rights for their own GitHub fork, but the owner will not have access to it.
7. Each team member will clone their GitHub fork on their local development computer (**the team member's local clone**).

## Branches

Each person working on the project will have at least three branches:

1. **`main`**  
   This will contain the most recent stable code for the project that is delivered to the end-users.
   
   No code will be added to `main` unless it has been **carefully checked and validated** by the project leader or by consensus with the whole team. (It is not good for business to release buggy code to the end-users.)

2. **`dev`**  
   This will contain the code that is destined to become the next version of `main`. It *should* be free of bugs, but it may contain new features that are still incomplete.
   
   New code will be added to `dev` on a regular basis, but only after it has been peer-reviewed by at least one other senior person on the team. (That person may be you.)

3. **`branch-with-a-custom-name`**  
   When code is added to the `dev` or the `main` branches, the addition should be done by *merging* code that has already been tested. No-one should *edit* the code in `dev` or `main` directly.

   This means that all actual work should be done in a different branch, and the name of the branch should describe the work that is being done. For example: if you are asked to add a landing page for the web site, you could create a specific branch called `landing-page`. If you are asked to fix some CSS issues, your specific branch could be called `css-update`. You should only work on one particular aspect of the project in any given branch.

## Workflow

Initially, the project will start with a `main` branch that might contain some boilerplate starter code. The project owner will then create a `dev` branch from `main`. Each team member will create a fork and a clone which contain these two branches.

After a first team meeting, each team member (you, for instance) will choose a feature (topic) to work on, and create a specific branch for that topic. You can work on your topic, making a new commit each time you finish a sub-unit of your work. When you feel confident that you have completed your task, you can *push* your branch to your team member's fork.

This is where GitHub gets to use its own magic to help you.

On your repository on GitHub, a special page will be automatically created to allow you to create a *Pull Request* (PR). A pull request suggests that the project owner (or other team members) *pull* your new branch to their local clones, so that they can test whether your code works as expected and fits in well with the features that they are working on.

You can continue to work on another topic (in a different branch with a new descriptive name), while you are waiting for approval for the work that you have just submitted.

## Approval

If you are the project owner, one of your tasks will be to review the PRs submitted by the team members. You can pull your team member's branch from their GitHub fork to your local development computer and merge your `dev` branch into it. 

**Note that your `dev` branch will remain unchanged: it is the new branch which will receive any recent changes that have been made to the `dev` branch.**

You can then test if it the merged branch works as planned.

If it doesn't work exactly as planned, you can discuss any issues with the team member. The Pull Request page on GitHub provides a convenient place to exchange messages about any changes that need to be made.

When you are happy that the new branch is stable and working well, you can update `dev` by merging the new branch into it. You can then push this updated `dev` branch to your (owner's) GitHub repository... and inform all team members that `dev` has been updated.

All the team members can now pull the new version of `dev` from the owner's "source of truth" repository, and merge it into whichever custom branches they are working on.


## Avoiding Conflits

This workflow ensures that all team members can work on different parts of the project at the same time, and continually update their copy of the project, each time a new pull request is approved.

Typically, a project will be designed to be _modular_. The project will be broken down into different sections. Each section will be stored in a different set of files, most probably in their own folder. Each team member will be working on a different feature from the others, and therefore will be working on a different set of files.

Git is designed to handle this modular arrangement for you elegantly.

However...

Sometimes, two people may be forced to make changes in the same place in the same file. Git is a piece of software; it has no human capacity to think and take decisions. Git cannot know which change to keep and which to refuse. This leads to what is called a _merge conflict_.

[Back to the README](./README.md)