# In-depth Tips

Replit's tutorial system basically creates a markdown book (with an optional acompanying video) that will run next to the student's IDE.

The best way to start is just to get your finished project running correctly with the RUN button. Your intro slide should have the student click RUN to see the completed version of what they'll be building. This also gives you a good starting point for building the tutorial.

## Getting the Completed Project Running

### How Replit loads packages

Replit uses NIX on the backend to hot load binaries as needed into your Repl. This means that whenever you need a binary, the best way to get it is to either

1. just try running the binary from the shell
2. Open the `replit.nix` hidden file and add the binary to the dependencies

Let's try this by adding `pkgs.just` to the `replit.nix` file. Then open a new shell and run `just`, the binary should be loaded and give an output.

### Getting your project running

Replit SHOULD be able to run your project just out of the box, but if you run into issues just hack on it for a little while or reach out to Kody for support. Some tips: 
1. try running whatever command you normally use to run the project from the Shell, that tends to work better
2. Use the "secrets" tool in replit instead of a .env file, you just set your environment variables as key value pairs
3. Set your nix channel to `unstable` in the `.replit` file and confirm against the nix package registry for the specific packages and versions you need.

## Breaking down the completed project

Take your completed project and try to break it down into sections that'll take about 10 minutes each. Each of these sections will become a `.md` file in the `.tutorial` directory. and should be laid out as such:

```
# Top Level Header: One Senctence Description of what the student will do in this section

1-2 sentences elaborating on what they'll do if necessary

## Starter Code
A code block (3 back ticks to open and close) with the segment of starter code or function/class handles

TODO:
- [ ] Try running this command...  

you should get this output/error:

Output or error they'll see

## Context for how to fix the error or do the next steps

Paragraph descriptions of how to do the next steps

...

...

...

## TODO: Build this / Fix this
- [ ] First thing to do
    - Tip 1
    - Tip 2
- [ ] Second thing to do
    - Tip 1
    - Tip 2

#### When you're done, you should be able to run ...

`just command from earlier`

and get this output ...

`output`

To see the solution, go check `tutorial-solution/foo/bar.py`

Onto the next step!!

```

## Using `just`

`just` is a super simple command runner. It's like `make` but better.

Create a file in the root directory called JUSTFILE.

The format of the JUSTFILE will look like this:

```
one:
    echo 'running a very complex command by just typing `just one` instead of having the student copy a bunch of things'

two:
    echo 'running a different complex command without the user having to set a bunch of flags or whatever'
```

Just is a super easy way to make sure the student runs exactly the commands you want them to using the configs you want them to at the beginnings and ends of sections!