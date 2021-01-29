## Ask your WebDev if iTermocil is right for you! 

Five hours ago, I would have guessed that iTermocil is a prescription medicine you'd hear about on a late night TV commercial that ends with "talk to your doctor if iTermocil is right for you!"

But nope, not even close. (Thankfully!)

Earlier tonight, a [tweet by Cam Sloan](https://twitter.com/SloanCam/status/1354884078496083968) caught my eye. Cam is a former co-worker from *ecobee* who has since made the leap to being an indie hacker with [Hop Scotch](https://hopscotch.club/). Before you read any further, take a moment to follow him on Twitter.

*iTermocil* is a command line tool that allows you to "setup pre-configured layouts of windows and panes in iTerm2". Here's why that matters.

iTerm2 is an alternative for the Terminal app that comes bundled up with a Mac. I was introduced to it about a year ago by a developer on my team when he saw me switching between Terminal tabs one too many tabs. iTerm2 is highly customizable. It allows you to open multiple windows (tabs) and panes (sections) in a single iTerm2 window, with full reign over the color scheme as well.

This is a slightly over-the-top example from [/u/Erentigionation](https://www.reddit.com/r/unixporn/comments/85egh0/iterm2_with_tiling_windows_and_custom_green_theme/) on reddit.

![iTerm2](https://imgur.com/j8MXRnC.png)

As you can see, this window has 5 panes on it: 3 across the top row and 2 on the bottom.

Here's the problem that iTerm2 solves:

Can you imagine recreating your panes across multiple windows every time you restart your computer or close iTerm2? 

Honestly my iTerm2 window setup is a deterrent for me for restarting my computer. It's not just recreating the panes, but configuring the environments in each of them. I have an iTerm2 setup that I use daily that includes 3 panes, each with a different virtual environment. It's a pain (pun intended, sorry) to figure out which virtualenv to setup on each pane. I was lamenting this just this evening. 

iTermocil to the rescue.

### Install iTermocil:

The [iTermocil project on GitHub](https://github.com/TomAnthony/itermocil) is well-documented, with several examples ready for you to copypasta. The steps outlined there are easy to follow. Here's a sample which shows you just how easy it is to install.

```bash
# Install `itermocil` via Homebrew
$ brew update
$ brew install TomAnthony/brews/itermocil
```

### Create configuration file:

Once you've installed iTermocil, the key is to create a .yml file that will configure the layouts of your windows and panes. I only need one window with 3 panes. Let's callt his `guac.yml`.

* The `main-vertical` layout is pre-configured and covered in the examples on the docs. It sets up a window with 2 columns, with the second column split horizonally into two.

* The `root` variable points iTerm2 to your working directory.

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


### Run to automatically configure iTerm2:

I can comfortably restart my computer now because I can rest assured that my iTerm2 setup will be up and running with a short `itermocil guac` command. Replace `guac.yml` with the name of your .yml config file.

That's it.

