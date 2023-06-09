# Kody's Tips for Making Great Replit Tutorials/Workshops

Thanks so much for prepping a workshop on Replit! Replit can be hard to use sometimes, but I promise getting the workshop running here is a huge service to the students and future audience of your workshop. 

Replit as a nix-based in-browser IDE means you have reproducible, deterministic builds for your tutorial/workshop's programming environment. If you can run it, so can the students, even if they're using Windows machines or on mobile!

These are all recommendations, feel free to approach with your own flavor or ignore them entirely. If you don't want to use Replit at all or don't have time to switch over, please check with Kody so that he can see about turning your tutorial into a Repl himself for distribution after your workshop.

The following is a step by step guide for creating a really high quality Replit tutorial. I've also put some general tips at the end that I've found helpful creating workshops and tutorials in the past. The whole process of taking a completed project and turning it into a tutorial should take about 1-2 hours (depending on the complexity of the project).

It'll be EXTREMELY helpful if you send me (`@kody` on Replit) a multiplayer link to your Repl after you've worked on it for about an hour to let me know any issues or snags you've hit so I can jump in early. Replit's tutorial system is still a little rough around the edges but I've been helping a ton of people with them so can probably help you out really quickly. 

## Step by Step Guide for Making a Replit Tutorial

### Part 1: Setting up the Code

1. Start with a working final project, completed code, or whatever the ending version of the code is as a github repo.
2. Import the project as a Repl (replit will autoID the required dependencies) or make a new Repl `https://replit.com/new` in the primary language your project will be then clone it down using the `git` command line tools.
3. Reverse engineer the project conceptually into 10-ish minute chunks of work, either from beginning -> end or end -> beginning
4. VERIFY THAT THE PROJECT RUNS CORRECTLY.
    - You can configure the `RUN` button in the Repl by changing the first config in the `.replit` file. (Click the 3 dots in the file tree to "Show Hidden Files" to see it).
        - I recommend you also change the `nix channel` to `"unstable"` to use the most recent binary versions for all your dependencies and languages.
    - Hack at the Repl until the project works. This WILL be hacky for some projects, if you run into issues please let me know and I can help.
    - Once you get the project running, commit it to a new `tutorial-solution` branch. Getting the project running successfully in Replit is very important, please don't accidentally have to do it twice :D
    - Now make another branch just called `tutorial` where we'll be building out the rest of the tutorial. We'll clone the solution down again at the end, but this `tutorial` branch is what we'll work on.
4. Make a directory called `.tutorial` at the root of the project
    - The filetree will collapse when you make this, just hit the button in the top left to pop it back open.
5. Make a markdown file in that `.tutorial` dir for each 10-ish minute chunk of work with:
    - Chunk of work you're doing: level 1 header and 1-2 sentences 
    - Starter code snippet: level 2 header and codeblock with comments. This can be the completed code from the previous md file or a new section of code.
    - Steps to complete the starter code
    - Specific ToDo's or tests to run before continuing to the next part of the tutorial
6. Move code FROM the completed project TO the .md files and fill in the .md file structure of the tutorial
    - You can either go beginning -> end or end -> beginning, I've found it relly depends on the project/language which one is more effective. What's normally important is that you want the ending code of each section to be testable/runnable if possible so the student knows that they're on the right track.
    - Either:
        - Write tests using the Replit Testing Tool (this is pretty buggy I've found)
        - Make a `JUSTFILE` with `just` commands to run at the end of each .md page's code as a test. If you've never used `just` before it's like `make` but more awesome.
7. Make an `.tutorial/00-intro.md` file as a front page for the project.
8. Clone or copy down the completed solution, the `tutorial-solution`, the completed code we had earlier, into the tutorial and rename it as `tutorial-solution` or `final-code` or something
9. Change the RUN command again in the `.replit` file to run the tutorial solution. This is very important because the Preview screen for the tutorial allows the user to hit RUN, and you want that to show what the FINAL version of the code will do not the starter version which will probably throw an error.
    - I've also found it useful to make some modifications to the solution's RUN to print out something like "Fork this repl to get started!" or "Fork this Repl to learn to build me!" for getting people to actually do your tutorial.

### Part 2: Doing it live! (and embedding the video)

After you've got the tutorial working the way you want, I recommend you try to run through the whole thing yourself. There'll probably be some bugs you'll find and address.

You're now ready to run your workshop! We'll be recording the workshops so if it goes well and you like how it went we'll just use that. If you run into a snag or just would prefer to make a more formal, prerecorded video that works great to and we'll use that! Think of the live workshop as more of a "We'll do it live!" where we WANT to play, debug, interact with the audience, and find issues. Then afterward you can record a final video (if you want) methodically doing the tutorial as intended.

To actually put the video into the replit tutorial:

1. Upload the video to youtube.
2. Get the `embedUrl` link.
3. Create a `video.json` file in `.tutorial` dir 

and populate the `video.json` file with:
```
{
    "embedUrl": "https://youtu.be/embedvideourl"
}
```

and that's it! Refresh the repl and you should see that the tutorial video pops open as well as the markdown tutorial!

### Thank you so much for doing this, we really appreciate your help and work to make this hackathon a success!

The following slide has additional tips and guidance on each one of the steps above. They're totally optional, I just thought they'd be helpful as a reference for how to make a tutorial yourself!

Please don't hesitate to just contact Kody (@kody on Replit, kody@fedi.xyz email, kodylow#5554 on discord, kodylow on twitter) and I'll schedule a call to pair program wiht you and help you get over any hurdles you run into!!!