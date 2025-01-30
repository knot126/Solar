# Solar Automatic Deobfuscation Project

I would like to deobfuscate an ARM64 Mach-O file which is heavily obfuscated. Unfortunately, there do not seem to be any high quality automatic deobfuscation tools available to the public.

## Research

*To be clear: I have no idea what I'm doing! Go read some papers if you want an idea of how to do this seriously.*

I am considering implementing a limited, static-ified variant of the core idea described in [*A Generic Approach to Automatic Deobfuscation of Executable Code*](https://www2.cs.arizona.edu/people/debray/Publications/generic-deobf.pdf) (that is, view some code as taking inputs and producing outputs, then simplifying the program from there) implemented over Ghidra's Pcode, though I'm not sure how well it would work. I would love to see if someone has already done something like this. Maybe it would also be possible to make an emulator so we could get full dynamic information?

To be honest, an implementation of [*SATURN: Software Deobfuscation Framework Based on LLVM*](https://arxiv.org/pdf/1909.01752) would probably take the least effort and theoretical understanding (which I lack sadly), be easier and actually produce better results. Plus binary rewriting just sounds cool and is tool-agnostic.

I have seen [*An Abstract Interpretation-Based Deobfuscation Plugin for Ghidra*](https://www.msreverseengineering.com/blog/2019/4/17/an-abstract-interpretation-based-deobfuscation-plugin-for-ghidra); using the plugin would be nice, but it should be noted that it hasn't been updated in years. (Though maybe thinking about this approach is better than the first thing I mentioned? Given that it's more suited to static analysis.)

I've looked into using Maism, as described in [*Deobfuscation: recovering an OLLVM-protected program*](https://blog.quarkslab.com/deobfuscation-recovering-an-ollvm-protected-program.html). Sadly it seems like they don't support Mach-O format files, and while I could add support for Mach-O's I don't think that sounds very fun and it's not my preferred solution.

I have also found the [FairFree project](https://github.com/roothide/FairFree) who seem to have cracked the DRM and used a "powerful deobfuscation tool" that was "donated to them". I wonder what that was...

I do wonder if a combination of abstract interpretation and taint analysis would work? Just intuitively, it feels like that would be pretty good at simplifying programs, even if it's only an interprocedureal (one function at a time) implementation.
