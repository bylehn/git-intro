  - How can we find out when exactly a line of code was changed?
  - "`git log/grep/annotate/show/bisect` is a powerful combination when doing archaeology in a project."
Please make sure that you do not clone repositories inside an already tracked folder:
$ git status
If you are inside an existing Git repository, step out of it.
You need to find a different location since we will clone a new repository.
If you see this message, this is good in this case:
fatal: not a git repository (or any of the parent directories): .git
## We will use the following four commands
### `git grep`
With `git grep` you can find all lines in a repository which contain some string or regular expression.
This is useful to find out where in the code some variable is used or some error message printed. Example:
$ git grep sometext
### `git show`
We have seen this one before already. Using `git show` we can inspect an individual commit if
we know its hash:
$ git show somehash
### `git annotate`
Try it out on a file - with `git annotate` you can see line by line who and **when** the line was modified
last. It also prints the precise hash of the last change which modified each line. Incredibly useful
for reproducibility. Example:
$ git annotate somefile
### `git checkout -b` to inspect code in the past
We can create branches pointing to a commit in the past.
This is the recommended mechanism to inspect old code:
$ git checkout -b branchname somehash
Example:
> Let us explore the value of these commands in an exercise. We recommend that you
> do this exercise in groups of two and discuss with your neighbors.
>
> 1. Clone this repository:
>    [https://github.com/tidyverse/rvest](https://github.com/tidyverse/rvest).
>    Then step into the new directory:
>    ```
>    $ git clone https://github.com/tidyverse/rvest.git
>    $ cd rvest
>    ```
> 2. Find the code line which contains `'No links matched that expression'`
> 3. Find out when this line was last modified. Find the actual commit which modified that line.
> 4. Inspect that commit with `git show`.
> 5. Create a branch pointing to the past when that commit was created to be able to browse and use the code as it was back then.
{: .challenge}
## Finding out when something broke with `git bisect`

> ## How would you solve this?
>
> Before we go on first discuss how you would solve this problem.
{: .discussion}

>
>
> #### Bonus exercise
{: .challenge}