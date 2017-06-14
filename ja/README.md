# Syntax guide

Here’s an overview of Markdown syntax that you can use anywhere on GitHub.com or in your own text files.

## Headers

# This is an `<h1>` tag

## This is an `<h2>` tag

###### This is an `<h6>` tag

    # This is an <h1> tag
    ## This is an <h2> tag
    ###### This is an <h6> tag
    

## Emphasis

*This text will be italic* *This will also be italic*

**This text will be bold** **This will also be bold**

*You **can** combine them*

    *This text will be italic*
    _This will also be italic_
    
    **This text will be bold**
    __This will also be bold__
    
    _You **can** combine them_
    

## Lists

### Unordered

* Item 1
* Item 2 
  * Item 2a
  * Item 2b

    * Item 1
    * Item 2
      * Item 2a
      * Item 2b
    

### Ordered

  1. Item 1
  2. Item 2
  3. Item 3 
    1. Item 3a
    2. Item 3b

    1. Item 1
    1. Item 2
    1. Item 3
       1. Item 3a
       1. Item 3b
    

## Images

![GitHub Logo](/images/logo.png) Format: ![Alt Text](url)

    ![GitHub Logo](/images/logo.png)
    Format: ![Alt Text](url)
    

## Links

http://github.com - automatic! [GitHub](http://github.com)

    http://github.com - automatic!
    [GitHub](http://github.com)
    

## Blockquotes

As Kanye West said:

> We're living the future so the present is our past.

    As Kanye West said:
    
    > We're living the future so
    > the present is our past.
    

## Inline code

I think you should use an `<addr>` element here instead.

    I think you should use an
    `<addr>` element here instead.
    

# GitHub Flavored Markdown

GitHub.com uses its own version of the Markdown syntax that provides an additional set of useful features, many of which make it easier to work with content on GitHub.com.

Note that some features of GitHub Flavored Markdown are only available in the descriptions and comments of Issues and Pull Requests. These include @mentions as well as references to SHA-1 hashes, Issues, and Pull Requests. Task Lists are also available in Gist comments and in Gist Markdown files.

## Task Lists

* [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
* [x] list syntax required (any unordered or ordered list supported)
* [x] this is a complete item
* [ ] this is an incomplete item

    - [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
    - [x] list syntax required (any unordered or ordered list supported)
    - [x] this is a complete item
    - [ ] this is an incomplete item
    

If you include a task list in the first comment of an Issue, you will get a handy progress indicator in your issue list. It also works in Pull Requests!

## Tables

You can create tables by assembling a list of words and dividing them with hyphens - (for the first row), and then separating each column with a pipe `|`:

| First Header                | Second Header                |
| --------------------------- | ---------------------------- |
| Content from cell 1         | Content from cell 2          |
| Content in the first column | Content in the second column |

    First Header | Second Header
    ------------ | -------------
    Content from cell 1 | Content from cell 2
    Content in the first column | Content in the second column