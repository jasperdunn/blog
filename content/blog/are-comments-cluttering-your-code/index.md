+++
title = "Are comments cluttering your code?"
description = "This practice is often taught and encouraged at UNI or College. However, is this the most effective approach to communicate?"
date = 2021-03-27T05:29:00Z

# The weight as defined on the Section page of the documentation.
# If the section variable `sort_by` is set to `weight`, then any page that lacks a `weight`
# will not be rendered.
weight = 0

# A draft page is only loaded if the `--drafts` flag is passed to `zola build`, `zola serve` or `zola check`.
draft = false

# Use aliases if you are moving content but want to redirect previous URLs to the
# current one. This takes an array of paths, not URLs.
aliases = ["comment-clutter"]

# When set to "true", the page will be in the search index. This is only used if
# `build_search_index` is set to "true" in the Zola configuration and the parent section
# hasn't set `in_search_index` to "false" in its front matter.
in_search_index = true

# Template to use to render this page.
template = "page.html"

# The taxonomies for this page. The keys need to be the same as the taxonomy
# names configured in `config.toml` and the values are an array of String objects. For example,
# tags = ["rust", "web"].
[taxonomies]
categories = ["programming"]
tags = ["dx"]

# Your own data.
[extra]
image = "my-dog.jpg"
image_alt = "A photograph of a cat incorrectly labelled “my dog”."
+++

Writing code involves communication between you, a computer, and other humans.

When we write code, we give another developer instructions describing what we want the computer to do.

A developer needs to place themselves in the authors' shoes and understand their thoughts. For this to work, the author must write clearly and explicitly.

Often while developing, we come across projects cluttered with comments describing nearly every line of code. This practice is often taught and encouraged at UNI or College. However, is this the most effective approach to communicate?

Does adding information above our functions and variables help us to get the message across?

Could we write our code so that it is easy to understand in isolation, without the need for these often unnecessary descriptions?

> "Programming is the art of telling another human what one wants the computer to do."<br />- Donald Knuth

Let's look at some basic scenarios.

The variable names below aren't self-explanatory, so the author has added comments to describe what the code does.

```ts
// this function deletes a banana
function remove() {}

// sends username and password of the admin to the create user api
function createNew(id, pass) {}
```

Let's improve the variable names.

```ts
// this function deletes a banana
function deleteBanana() {}

// sends username and password of the admin to the create user api
function createAdminUser(username, password) {}
```

Now that the code has meaningful variable names, are these comments helping the reader to understand the code?

These type of comments aren't necessary and use up extra brainpower whilst deciphering the code.

Here we have the same functions without the comments.

```ts
function deleteBanana() {}

function createAdminUser(username, password) {}
```

What does `deleteBanana` do? It deletes a banana... obviously!
What does `createAdminUser` do? It creates an admin user! 😝
If a variable name makes sense outside of the code's context, it's a good name.

> "Code is like humour.<br />When you have to explain it, it's bad."<br />- Cory House

There is growing usage of _handy_ comment-generating libraries; unfortunately these also duplicate information and increase incoherence.

There is nothing more confusing than trying to understand code that describes the same thing differently in two places.

Below are some typical examples of such a library in practice.

```ts
// Deletes the Fruit entity with the specified fruitId.
function deleteFruit(int fruitId) { }

// The class definition for the FruitBowl entity.
class FruitBowl {
    // The Banana of the FruitBowl entity.
    static banana
}

// Creates the Admin User entity.
function createAdminUser() { }
```

Here a developer has modified the functionality yet has forgotten to update the description. Perhaps the new function can create any type of user. However, the comment asserts that it creates admin users. Which is correct?

```ts
// Creates the Admin User entity.
function createUser(userRole) {}
```

Often comments are not updated as the code changes, and these outdated comments will confuse and distract future developers.

---

In summary, I encourage you not to write pointless comments. They often make the code bloated and more challenging to read.

If a fellow developer comes across a comment, the chances are that they'll spend unnecessary time trying to understand the author's intention.

Comments aren't required when the code is written with correct variable names; ones that give meaning outside of context.

Aim to write only what is required for the reader to understand the code.

Thanks for being here! Happy coding! ☺️
