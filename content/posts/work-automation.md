---
title: "Work Automation"
date: 2020-08-03T22:47:49-05:00
tags: [automation, bash, cli]
featured_image: ""
description: "How I automate the start and end of my work day"
draft: true
---






___

#!/bin/bash

# Open applications need to start your work day

open -a "Google Chrome.app" https://tomato-timer.com https://www.pivotaltracker.com/n/projects/2353404

open -a "Slack.app"

open -a "IntelliJ IDEA.app"

open -a "Insomnia.app"

open -a "Sublime Text.app"

open -a "Microsoft Outlook.app"


#!/bin/bash

# Close all work applications, work is over

killall Slack
killall Insomnia
killall idea
kill $(pgrep zoom)
kill -9 $(pgrep Outlook)
kill $(pgrep AnyConnect)
kill $(pgrep webex)

# Close all unpinned tabs in Chrome
osascript -e 'tell application "Google Chrome" to activate' && osascript -e 'tell application "System Events" to keystroke "o" using {shift down, option down}'