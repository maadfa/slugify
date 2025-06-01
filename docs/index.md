
# Slugify –  Documentation Edition

## Table of Contents
- [Slugify –  Documentation Edition](#slugify---documentation-edition)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [How to  Install](#how-to--install)
    - [**Usage**](#usage)
  - [Basic Usage](#basic-usage)
  - [Explanation](#explanation)
  - [Customizing](#customizing)
  - [Example of Customization](#example-of-customization)
  - [Locales](#locales)
  - [Extend](#extend)
  - [Contribute](#contribute)

## Introduction
**Slugify** is a powerful tool that converts any string into a URL-friendly slug. This is particularly useful for web applications, blogs, and search engine optimization (SEO). For example, the string "Hello World!" would be transformed into "hello-world".

## How to  Install
There are few ways to install terminall .Open your terminal and run the following command

It can be installed by using yarn .Enter the following command on your terminal

```
yarn add slugify
```

It can also be installed by using npm:

```bash
npm install slugify 
```


###  **Usage**

## Basic Usage
1. Import the Slugify Module

```javascript
const slugify = require('slugify');
```

2. Convert a String into a Slug
   
 ```javascript
   const slug = slugify('Hello World!');
 ```  
 3. Print the Result to the Console
   
 ```javascript
   console.log(slug); // Output: hello-world
 ```  

## Explanation

The require('slugify') statement imports the Slugify module into your file, allowing you to
 use its functionality.

The slugify('Hello World!') function call transforms the string into a slug by:
Replacing spaces with dashes (-)

Converting all letters to lowercase



## Customizing 

You can customize the behavior of Slugify by passing an options object. Here’s how:

## Example of Customization


You can customize  or change the setting or  the behavior by passing an options object:

<pre> !!! info 
```js slugify('Hello World!', {

  replacement: '-',    // Replace spaces with this character (default: '-')

  remove: /[*+~.()'"!:@]/g, // Remove these characters (RegEx)

  lower: true,         // Convert to lowercase (default: false)

  strict: true,        // Remove anything not allowed in URLs (default: false)

  locale: 'vi',        // Set locale (for language-specific transliteration)

  trim: true           // Trim leading/trailing separators (default: true)
});``` </pre>
 
 
 ## Remove Characters

  Special characters Can be removed by  using the remove option.

```js
  slugify('Hello *World*!', {
  remove: /[*+~.()'"!:@]/g
});
// Output: Hello-World
```

For example, to remove `*+~.()'"!:@` from the result slug, you can use 

```js
slugify('..', {remove: /[*+~.()'"!:@]/g})`.
```
**If You Use a RegEx**
 If you use RegEx,Use only a character class . Write all the characters you want to remove inside square brackets.

 **Input**

 ```js
 const slugify = require('slugify');

const text = "Hello! This+is*a~test(string)with@special:characters.";

const result = slugify(text, {
  remove: /[*+~.()'"!:@]/g,
  lower: true
});

console.log(result);
```


**Output**

This will result in following output


 ```js
 hello-thisisateststringwithspecialcharacters
 ```

**If You Use a string**
If you decide to use string 
**Input**

```js
 const slugify = require('slugify');

const text = "Hello! This is amazing!";

const result = slugify(text, {
  remove: '!',  
  lower: true
});

console.log(result);
```

**Output**

The output recieved will be without (!)

```js
hello-this-is-amazing
```


## Locales
When you convert a string to a slug, slugify replaces special or foreign characters (like é, ö, or ñ) with their closest English equivalents.Slugify uses a file called charmap.json. This file contains a big list of characters and their English versions.Let’s say charmap.json turns a letter into the wrong English letter for your language. For example, in Vietnamese or Turkish, some characters might have different meanings or sounds.You don’t change charmap.json directly.Instead, you add a custom correction in another file called locales.json



The main file called `charmap.json` has a list of all characters and how they should be changed into English letters. If you find a new character that isn't in this file, you should add it there first.

If you come across a character that is already in `charmap.json`, but it doesn't translate correctly for your language, you can fix this by adding that character to another file called `locales.json`. This way, you can change how that character is translated, but only for your specific language.

You can get the correct language code of your language from [here](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).

## Extend

Slugify comes with support for a limited set of Unicode symbols. If you want to add support for additional symbols or override existing ones, you can use the extend method.Out of the box `slugify` comes with support for a handful of Unicode symbols.

```js
slugify('unicode ♥ is ☢') // unicode-love-is
```

However you can extend the supported symbols, or override the existing ones with your own:

```js
slugify.extend({'☢': 'radioactive'})
slugify('unicode ♥ is ☢') // unicode-love-is-radioactive
```

When you use slugify.extend(), it adds or changes how characters are replaced  for the entire project.

If later you want to undo those changes and start fresh, you need to clear the module from memory (called the "cache") . Otherwise, it keeps using your changes


```js
delete require.cache[require.resolve('slugify')]
var slugify = require('slugify')
```

## Contribute

If you want to contribute to Slugify, here are the steps you can follow:

Add characters to charmap.json.

Run tests using:

```
npm test
```

The tests will build the character map in index.js and sort the charmap.json.
Commit all modified files

Slugify is a versatile and easy-to-use tool for generating URL-friendly slugs from strings. With its customization options and support for various locales, it can be adapted to meet the needs of different projects. Whether you're a beginner or an experienced developer, Slugify can enhance your web applications and improve SEO.





