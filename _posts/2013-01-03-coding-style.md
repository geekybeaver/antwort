---
layout: guide
title: Coding Style
category: how
description: Basic differences and best practices when writing HTML for email clients instead of websites.
---


# General Coding Tips

Antwort and these tips were written for experienced Email HTML developers. Much of this won't really hit home until you're written an email.

If you're just starting, you should start here instead:
* [Campaign Monitor's Guide to Coding Emails](http://www.campaignmonitor.com/guides/coding/) - thorough introduction to writing HTML for Email.
* [Mailchimp Support how-to article on coding HTML Email](http://kb.mailchimp.com/article/how-to-code-html-emails) - shorter than the above novel.
* [Mailchimp's Email-jitsu](http://mailchimp.com/resources/guides/email-jitsu/) - entertaining read with practical tips.

Then come back here for some general coding style tips for HTML email.

## HTML
----

### 1. Use `<table>`s

Code like it's 1999 with tables. Do not use `<div>`s or floats for layout. Some versions of Microsoft Outlook use its own Word markup processing engine and require tables for layout.

### 2. Nest tables for complex layouts

Avoid `rowspan` altogether and minimize use of `colspan`. You may find yourself constantly tweaking your template and code legibility and flexibility is important here. It's far easier to copy and paste nested tables than figure out which columns go where.

### 3. Avoid semantic HTML tags e.g. `<p>`, `<h1>`, `<h2>` etc.

Use heading tags and suddenly your may find your heading text green, for example in Hotmail which uses these tags in their own markup.

To mimic appearance of paragraphs, I prefer double line breaks `<br><br>` over `<p>`s:

    <table>
        <tr>
            <td style="font-size:14px; font-family: Helvetica, sans-serif; color: #333;">

            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor
            incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud
            exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
            <br><br>

            Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu
            fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
            culpa qui officia deserunt mollit anim id est laborum.
            <br><br>

            </td>
        </tr>
    </table>
{: .language-markup}

Advantages

* Double line breaks `<br><br>` are consistently rendered across all email clients whereas some have custom margins or padding for `<p>`.
* Declare font styles **once** in a parent `<td>` tag instead of every `<p>`.
* Better readability of content

## CSS
----

### 4. Use inline CSS

There are various tools like [Mailchimp's CSS Inliner Tool](http://beaker.mailchimp.com/inline-css) to help you move your classes inline.

Personally, I don't use inliner tools. Most of the work in creating HTML emails is in testing and using an inliner tool just adds another step to the process. Once I have my layout and basic design, I handcode my CSS inline. Any classes used are then for mobile styles.


### 5. Avoid shorthand CSS property defintions

* Ok:

    `font: normal 12px/18px Helvetica, sans-serif;`{: .language-css}

* Better:

    `font-weight: normal; font-size: 12px; line-height: 18px; font-family: Helvetica, sans-serif;`{: .language-css}

Shorthand CSS properties generally work but the full definitions are more bulletproof especially on older email clients.


## Other technologies
----

I'm going to assume you're smart, so I will give you the TLDR version: just say NO to:

* Javascript
* Flash
* Video
* Forms
