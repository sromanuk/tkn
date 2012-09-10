# Terminal Keynote

![Terminal Keynote Cover](https://raw.github.com/fxn/tkn/master/screenshots/terminal-keynote-cover.png)

## Introduction

Terminal Keynote is a quick and dirty script I wrote for presenting my talks at [BaRuCo 2012](http://baruco.org) and [RailsClub 2012](http://railsclub.ru).

This is a total hack. It is procedural, uses a global variable, it has not been parametrized or generalized in any way. It was tailor-made for what I exactly wanted but some people in the audience asked for the script. Even if it is quick and dirty I am very happy to share it so I have commented the source code and there you go!

## Markup

Fuck markup, this is text going to a terminal. If you want a list type "*"s. If you want bold face or colors use ANSI escape sequences.

Slides are written in Ruby. See the examples folder.

## Syntax Highlighting

Terminal Keynote is text-based, but with style! Syntax highlighting is done on the fly with @tmm1's [pygments.rb](https://github.com/tmm1/pygments.rb). The script uses the "terminal256" formatter and "bw" style, the lexer is also hard-coded to "ruby". Since this was tailor-made it has not been factored out.

## Master Slides

There are four types of slides:

### :code

A slide with source code. Syntax highlighted on the fly. If you want to put a title or file name or something use source code comments and imagination.

![Terminal Keynote Code](https://raw.github.com/fxn/tkn/master/screenshots/terminal-keynote-code.png)

### :center

A slide whose text is centered line by line.

![Terminal Keynote Center](https://raw.github.com/fxn/tkn/master/screenshots/terminal-keynote-center.png)

### :block

A slide with text content whose formatting is preserved, but that is centered as a whole in the screen. Do that with CSS, ha!

I find centering content in the screen as a block to be more aesthetically pleasant that flushing against the left margin. There is no way to flush against a margin.

![Terminal Keynote Block](https://raw.github.com/fxn/tkn/master/screenshots/terminal-keynote-block.png)

### Sections

Sections have a title and draw kind of a fleuron. This is also hard-coded because it is what I wanted.

Sections allow you to group slides in your Ruby slide deck, and since they yield to a block you can collapse/fold the ones you are not working in for focus.

The nested structure is not modelled internally. The script only sees a flat linear sequence of slides.

![Terminal Keynote Section](https://raw.github.com/fxn/tkn/master/screenshots/terminal-keynote-section.png)

## Visual Effects

There is a hard-coded visual effect: Once the exact characters of a given slide are computed, we print char by char with a couple milliseconds in between. That gives the illusion of an old-school running cursor effect. Configure block blinking cursor for maximum awesomeness.

## Installation

By now this is not going to be a gem, please clone the repo and hack your talk. In its current state it is just too tailor-made for anything but personal forks. Please keep the script together with the slides, that way you guarantee one year later the presentation will still run.

If Terminal Keynote evolves it is going to do so in backwards incompatible ways for sure. So, let's wait. If the thing ever converges to something that can be packaged then I'll do it.

## Keyboard Controls and Remotes

* To go forward press any of " ", "n", "k", "l", PageDown (but see below).

* To go backwards press any of "b", "p", "h", "j", PageUp (but see below).

* Beginning of the talk: "^"

* End of the talk: "$"

My Logitech remote emits PageDown and PageUp. You get those as ANSI escape sequences "\e[5~" and "\e[6~" respectively. The script understands them, but you need to [configure them in Terminal.app](http://fplanque.com/dev/mac/mac-osx-terminal-page-up-down-home-end-of-line) and also tell it to pass them down to the shell selecting "send string to the shell" in the "Action" selector.

## Font and Terminal Configuration

I used Menlo, 32 points. That gives 18x52 in a screen resolution of 1024x768.

For your setup: Find out the resolution of the projector of your conference (ask the organization in advance). Set the screen to that resolution, choose font size and maximize window. When you like how it looks, then run `stty size` and write down rows and cols.

Then, define in your terminal application a profile for the theme you like, and initial dimensions to those rows and cols. That way the terminal will launch with those dimensions no matter the screen resolution and you can hack your talk in your day to day with the native resolution, knowing how is going to look in proportion.

## Editor Snippets

A snippet for your editor is basic to write slides quickly. The extras folder has a snippet for Sublime Text 2.

## Cathode

[Cathode](http://www.secretgeometry.com/apps/cathode/) is perfect for this thing. But because of how it draws the text it doesn't do bold faces and may not be able to render some colors or Unicode characters. YMMV.
