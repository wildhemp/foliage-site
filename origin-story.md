# The origin story and the <del>bright</del> future

## Why-oh-why would I do yet another worktree orchestration app when so many exist?

First I would point out that when I started this, there were only something like 6 or 7 (that I knew of, anyway; I'm sure GitHub history would tell a different story).

The way it started was something like this: I was trying to use Conductor, which at that point was already a somewhat mature product, and somehow I didn't get the same results with it as I did using Claude CLI.
It was somewhat subtle, but I got better results for similar tasks in Claude CLI. I suspected the issue to be related to model configuration. Claude CLI let me define not just the model but also the effort separately, and I couldn't find the same option in Conductor.
Besides that, while I generally liked Conductor, some stuff was a bit cumbersome to do.

Really, at that point, I was happy with Claude CLI and mainly needed worktree management. It also occurred to me that Anthropic, OpenAI, and Google have teams working on the tools, and the CLIs already have almost everything I or others need. Plus, I also like TUIs (but I admit that PTYs can have a steep learning curve).

So, on a Friday afternoon I was like, let me ask Claude how I would go about doing something similar to Conductor, but instead of using a custom harness, just use a PTY and start Claude CLI.
In 15 minutes, I decided what it would look like, and in an hour I had a working version, which I started using right away. Then I found all the things that were hard, impossible, or not good and fixed them (vibe coded it).

I found this exhilarating. I didn't know Rust at all, I don't normally use React, and here was an app that used both and worked the way I wanted it.

I kept having new ideas on what features to add to make my life easier and added them. For like 2 weeks I regularly slept less than 6 hours. I added automations like parsing PR comments and fixing them automatically, and buttons for my most used prompts like rebasing and resolving conflicts (yeah, I could add a skill for this, I probably will do that too).
I added features like opening diffs, then files in general, support for Codex and Gemini CLIs, support for Windows and Linux (though this one mostly worked), etc., etc.

Then I got tired, and it worked kinda okay, and these two things made me slow down considerably. I needed a break because I couldn't keep up doing one and a half jobs, plus my life.

## Why not open source it

Yeah, I was going back and forth on this. The deciding factor was that I do have to deal with coordination on projects, repos, features, and whatnot in my day job, and very often it takes a lot away from the fun. And this would only work if and for as long as I had fun.
I was really afraid that if others accidentally found it and started adding or requesting stuff, it would make it not super fun anymore. The plan was, and still is, to make it open source eventually. Not that I think there's that much value in doing so; this is just one of thousands of similar apps.

## What I learnt along the way

* I can still have fun, even while vibe coding
* A lot of coding time is spent learning how a framework, SDK, or codebase works and starting to use it.
* Each agent kinda had a coding style very much in line with the company implementing it. Gemini was very Googly in a certain way and super bad at UI. Claude was really an agent primarily developed for coding, or at least felt like it, and kinda heavyweight at this point. Codex was/is a lot lighter and somewhere in between.
* The hardest problem I faced was how to recognize when the agent is done as opposed to just having some break or a subagent being done. Even with webhooks, Claude had a lot of problems implementing it right and handling edge cases. I guess here it would be helpful if I looked more deeply into it myself.
* While adding personas seemed like a good idea, in reality they don't work super well. Probably just need more time.
* Windows is still not easy for me to use, especially after being on Mac since 2009
* You have to actively use the thing you are developing to have a chance of making it usable
* Just putting up a page on the internet doesn't mean anyone will ever find it, or if they do, they will care (though, this I suspected)
* UI is still hard to get right

## Any long-term plans?

Plans, no, not really. Ideas, yeah, those I have.

### Ditch the CLIs...

... and use some open source harness instead.

This goes against the whole CLI idea I started with, and the reasons I started with it. But the thing is that using the CLI makes certain things hard or cumbersome. Like adding loops/automations.

Prompting works kinda well, but it has its problems and I haven't so far managed to coerce Codex or Claude to find a good solution. They are not super creative. A lot of it right now relies on time-based thresholds which, while they work most of the time, fail just enough that it makes it super annoying.
It also doesn't make for a good UX :/.

It would make a lot of more complicated things possible as well, stuff that doesn't even occur to me because, well, even simpler things don't work that well today. I could do a more integrated UI and wouldn't be limited to what the CLI developers had in mind or copied from each other.

### Just leave it behind and do something cloud based

I think most of the models are good enough now to really just go and work alone and figure shit out without needing too much supervision. I like to be hands-on and steer them along the way, but it is not always possible, and especially the review loop takes a lot of time and doesn't need a lot of interaction.
And I know that a lot of these exist. Somehow I don't like Claude's solution, and Devin's models are still lagging.

Plus, I'm curious, I like to learn by doing, and I feel like there are a lot of interesting problems there, and it would be super cool to see how far I can get.

This also requires using some harness, or implementing one, which is also an interesting problem and would let me understand a lot of things a lot better.

### Maybe add more features

* Proper local code review loop, because I feel like this could really speed things up
* Support for multi-repo sessions, though, from a UX and worktree management perspective this may not be super simple
* Add things like monitoring PR review requests and automatically doing reviews
* Fix annoying bugs

A lot of these would actually work better in a managed cloud environment, but would probably work well enough in the current app too, with the limitation that the computer going to sleep will stop the work. Which may actually be okay/fine.
