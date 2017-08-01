Create sophisticated formatting for your prose and code on GitHub with simple syntax.

## Headings

To create a heading, add one to six `#` symbols before your heading text. The number of `#` you use will determine the size of the heading.

```
# The largest heading
## The second largest heading
###### The smallest heading
```

## Quoting text

You can quote text with a `>`.

```
In the words of Abraham Lincoln:
> Pardon my French
```

In the words of Abraham Lincoln:

> Pardon my French

## Quoting code

You can call out code or a command within a sentence with single backticks. The text within the backticks will not be formatted.

```
Use `git status` to list all new or modified files that haven't yet been committed.
```

Use `git status` to list all new or modified files that haven't yet been committed.To format code or text into its own distinct block, use triple backticks. 

```
git status
git add
git commit
```

For more information, see "[Creating and highlighting code blocks.](https://help.github.com/articles/creating-and-highlighting-code-blocks/)"

## Links

You can create an inline link by wrapping link text in brackets `[ ]`, and then wrapping the URL in parentheses `( )`. You can also use the keyboard shortcut `command + k` to create a link.

```
This site was built using [GitHub Pages](https://pages.github.com/).
```

This site was built using [GitHub Pages](https://pages.github.com/).

## Section links

You can link directly to a section in a rendered file by hovering over the section heading to expose the link:

![Section links](https://help.github.com/assets/images/help/repository/readme-links.png)

## Relative links

You can define relative links and image paths in your rendered files to help readers navigate to other files in your repository. A relative link is a link that is relative to the current file. For example, if you have a README file in root of your repository, and you have another file in *docs/CONTRIBUTING.md*, the relative link to *CONTRIBUTING.md* in your README might look like this:

```
[Contribution guidelines for this project](docs/CONTRIBUTING.md)
```

GitHub will automatically transform your relative link or image path based on whatever branch you're currently on, so that the link or path always works. You can use all relative link operands, such as `./` and `../.` Relative links are easier for users who clone your repository. Absolute links may not work in clones of your repository - we recommend using relative links to refer to other files within your repository.

## Lists

You can make a list by preceding one or more lines of text with `-` or `*`.

```

- George Washington
- John Adams
- Thomas Jefferson
```

- George Washington
- John Adams
- Thomas Jefferson

To order your list, precede each line with a number.

```

1. James Madison
2. James Monroe
3. John Quincy Adams
```

1. James Madison
2. James Monroe
3. John Quincy Adams

You can create nested ordered and unordered combination lists by indenting lines by four spaces.

```

1. Make my changes
    1. Fix bug
    2. Improve formatting
        - Make the headings bigger
2. Push my commits to GitHub
3. Open a pull request
    * Describe my changes
    * Mention all the members of my team
        * Ask for feedback
```

## Task lists

To create a task list, preface list items with `[ ]`. To mark a task as complete, use `[x]`.

```

- [x] Finish my changes
- [ ] Push my commits to GitHub
- [ ] Open a pull request
```

- [x] Finish my changes
- [ ] Push my commits to GitHub
- [ ] Open a pull request

If a task list item description begins with a parenthesis, you'll need to escape it with `If a task list item description begins with a parenthesis, you'll need to escape it with :

```

- [ ] \(Optional) Open a followup issue
```

For more information, see "[About task lists.](https://help.github.com/articles/about-task-lists/)"
