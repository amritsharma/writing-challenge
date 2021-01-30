## Ask your WebDev if iTermocil is right for you! 

Five hours ago, I would have guessed that iTermocil is a prescription medicine you'd hear about on a late night TV commercial that ends with "talk to your doctor if iTermocil is right for you!"

But nope, not even close. (Thankfully!)

While doomscrolling on Twitter today, a [tweet by Cam Sloan](https://twitter.com/SloanCam/status/1354884078496083968) about iTermocil caught my eye. Cam is a former co-worker from *ecobee* who has since made the leap to being an indie hacker with [Hop Scotch](https://hopscotch.club/). You should follow him on Twitter to get a front row seat to his inspriring journey of building a self-funded business.

So what *is* iTermocil?

*iTermocil* is a command line tool that allows you to "setup pre-configured layouts of windows and panes in iTerm2". Here's why that matters.

iTerm2 is an alternative for the Terminal app that comes bundled with a Mac. I was introduced to it about a year ago by a developer on my team when he saw me switching between Terminal tabs one too many times. iTerm2 is highly customizable. It allows you to open multiple windows (tabs) and panes (sections) in a single iTerm2 window, with full reign over the color scheme as well.

This is a slightly over-the-top example of iTerm2 by [/u/Erentigionation](https://www.reddit.com/r/unixporn/comments/85egh0/iterm2_with_tiling_windows_and_custom_green_theme/) from reddit.

![iTerm2](https://imgur.com/j8MXRnC.png)

If you look closely, there are six panes in this window. 

Here's the problem that iTermocil solves:

Can you imagine recreating your panes across multiple windows every time you restart your computer or close iTerm2? 

Honestly, my iTerm2 window setup is a deterrent for restarting my computer. It's not just recreating the panes, but configuring the environments in each of them. I have an iTerm2 setup that I use daily that includes 3 panes, each with a different virtual environment. It's a pain (pun intended, sorry) to figure out which virtualenv to setup on each pane. I was lamenting that just this evening. 

iTermocil to the rescue.

### Install iTermocil:

The [iTermocil project on GitHub](https://github.com/TomAnthony/itermocil) is well-documented, with several examples ready for you to copypasta. The steps outlined there are easy to follow, so I won't re-write them here. Though this sample shows you just how easy it is to install.

```bash
$ brew update
$ brew install TomAnthony/brews/itermocil
```

### Create configuration file:

Once you've installed iTermocil, the key is to create a .yml file that will configure the layouts of your windows and panes. I only need one window with 3 panes. Let's call this `guac.yml`. By the way, you can create as many .yml files as you want for your different projects and needs. You aren't limited to just one.

This is what mine looks like:

```bash
windows:
  - name: avocado
    root: ~/path/to/your/dir
    layout: main-vertical
    panes:
      - commands:
        - conda activate pyEnv
        - echo "ready for './name-of-file.sh'"
        name: 'Work Project 1'
      - commands:
        - source guac/bin/activate
        - echo "ready for './name-of-file2.sh'"
        name: 'Work Project 2'
      - commands: 
        - cd subfolder
        - source venv/bin/activate
        - echo "ready for './name-of-file3.sh'"
        name: 'Work Project 3'
```

* The `main-vertical` layout is pre-configured and covered in the examples on the docs. It sets up a window with 2 columns, with the second column split horizonally into two.

* The `root` variable points iTermocil to your working directory.


### Run to automatically configure iTerm2:

I can comfortably restart my computer now because I can rest assured that my iTerm2 setup will be up and running whenever I run the short `itermocil guac` command. Replace `guac.yml` with the name of your .yml config file.

That's it.

Thanks again Cam for tweeting about this nifty tool.
