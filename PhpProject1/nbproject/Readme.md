```# Podia


## Setup

Install Vagrant (version 1.8.5 or compatible). On Linux environments it's recommended to install:

- `lxc`, `redir`, `dnsmasq` packages
- `vagrant-lxc` plugin to vagrant

## Preparing a Vagrantfile

Copy the Vagrantfile.sample into Vagrantfile and set your own:  
- memory size  
- cpu limit  
- PORT (for example: 8080, 80, etc.)  

## Running
```
```bash
vagrant up  #setup virtual machine
vagrant ssh #enter virtual machine using ssh
run         #start the application
```
```Then application is available under `localhost:PORT` in browser.

## GIT and Github stuff

### Branching

We use a so-called "GIT-flow", it's branching model that makes clear what, when and how. A detailed description is here: [Succesful git branching model](http://nvie.com/posts/a-successful-git-branching-model/). The most important thing here is that new branch should always start from develop and be merged into develop. During release develop is merged into master.

Branch names should always be created conforming to given format: `<task_nr>-<task_summary>`, where:

  - `<task_nr>` is a number if task in redmine
  - `<task_summary>` is a short description of task, ideally it should match 1 to 1 against task summary in redmine

E.g.: task #7927 Import Terms & Conditions, FAQ's, Contact, info should be resolved on branch `7927-import-terms-n-conditions-faqs-contact-info`.

### Commits

Every commit should contain code changes that are closed, working stage in terms of given task. Every commit message should conform to following format: `[<TASK_NR>] <changes-description>`.

#### Do
* Write the summary line and description of what you have done in the imperative mode, that is as if you were commanding someone. Start the line with "Fix", "Add", "Change" instead of "Fixed", "Added", "Changed".

#### Don't
* Don't end the summary line with a period - it's a title and titles don't end with a period.

#### Tips
* If it seems difficult to summarize what your commit does, it may be because it includes several logical changes or bug fixes, and are better split up into several commits using `git add -p`.

#### Example
E.g. there is a task #7927 Import Terms & Conditions, FAQ's, Contact, info. It can be divided into 2 stages: adding a migrations file, changing PHP code for sidebars

  - `[7927] Add migration file`
  - `[7927] Updated the code responsible for sidebar display`

Do, don't and tips are from [erlang/otp wiki](https://github.com/erlang/otp/wiki/Writing-good-commit-messages)

### Pull requests (PR's)

Developer after finishing his task should open PR from task branch into develop. If needed - PR should have additional note exaplaining some unclear things.

Every PR should have assigned whole team involved in task's project in _Reviewers_ and every available team member should make a code review. Last reviewer can merge PR if all reviewers have approved given PR.

PR with failing tests and linters has to be rejected.
```