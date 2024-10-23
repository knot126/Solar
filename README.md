# Deobfuscation project

I would like to deobfuscate an ARM64 Mach-O file which is heavily obfuscated.

## Research

I am considering implementing a limited, static-ified variant of the core idea described in [*A Generic Approach to Automatic Deobfuscation of Executable Code*](https://www2.cs.arizona.edu/people/debray/Publications/generic-deobf.pdf) (that is, view some code as taking inputs and producing outputs, then simplifying the program from there) implemented over Ghidra's Pcode, though I'm not sure how well it would work. I would love to see if someone has already done something like this. Maybe it would also be possible to make an emulator so we could get full dynamic information?

To be honest, an implementation of [*SATURN: Software Deobfuscation Framework Based on LLVM*](https://arxiv.org/pdf/1909.01752) would probably take the least effort and theoretical understanding (which I lack sadly), be easier and actually produce better results. Plus binary rewriting just sounds cool and is tool-agnostic.

I have seen [*An Abstract Interpretation-Based Deobfuscation Plugin for Ghidra*](https://www.msreverseengineering.com/blog/2019/4/17/an-abstract-interpretation-based-deobfuscation-plugin-for-ghidra); using the plugin would be nice, but it should be noted that it hasn't been updated in years. (Though maybe thinking about this approach is better than the first thing I mentioned? Given that it's more suited to static analysis.)
