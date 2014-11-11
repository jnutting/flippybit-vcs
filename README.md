FlippyBit-VCS
-----

This is an Atari VCS (2600) port of [FlippyBit][flippybit-ios], a Flappy Bird
clone that was originally released for iOS in early 2014. FlippyBit is styled to
look like an old Atari game, so at some point the idea of porting it to the VCS
became inevitable. The source code for the VCS version is in `flippybit.dasm`.

![FlippyBit gameplay screenshot](screenshot.png)

Precompiled Binary
-----

This repo includes a precompiled binary (`flippybit.bin`) which can be run
directly in any VCS/2600 emulator, such as [Stella][stella].

Building (Easy)
-----
If you want to go the easy route, just grab [Ian Bogost's installer][ib_installer]
that includes a [TextMate][textmate] bundle which gives you 6502 assembly syntax
coloring, commands for building and running, and more. You'll also want to
install [Stella][stella].

Building (Hard)
-----
If you won't or can't use [TextMate][textmate], or want to do this all by hand for any other
reason, You'll need to do roughly this sequence of things:

- Acquire and install [dasm][dasm] for your platform of choice
- Put `vcs.h` and `macro.h` (included in this repo) in some sort of reasonable
  location for header files
- Build:
```
    /path/to/dasm flippybit.dasm -I/path/to/includes -f3 -s"flippybit.sym" -l"flippybit.lst" -o"flippybit.bin"
```

Following those steps should generate the binary itself, along with a symbol
file (useful for debugging with [Stella][stella], and a complete listing with all
macros expanded.

Known Issues
-----

The game isn't really complete. There's no start screen, no scoring, and no real
end game. Your flipping bit doesn't die when it hits a wall, it just turns black
during the collision. Also, the positions of the wall gaps aren't really
randomized as they should be. If you feel like completing these details, pull
requests are welcome!

[flippybit-ios]: http://www.rebisoft.com/software/flippybit.html
[stella]: http://stella.sourceforge.net/
[ib_installer]: http://bogost.com/writing/blog/atari_vcs_programming_in_textm/
[textmate]: http://macromates.com/
[dasm]: https://github.com/munsie/dasm
