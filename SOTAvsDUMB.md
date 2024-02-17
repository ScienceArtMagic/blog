# "How can we beat SOTA by 0.1?" v3248520562918938704 vs. "That's just dumb enough to work!" (a.k.a. "Why can't I find any papers like this?")

Am I the only one who feels like the numerous advances in rotary position embeddings (RoPE), no matter how elegant some of them may be, are ultimately just bandaids? I don't claim to have the answers. Still, I do know that a few papers (very few, from what I can find) investigate whether positional embeddings (PE) are required at all and, in a few cases, find that models NOT using PE generalize context length better than their counterparts with absolute (APE), relative (RPE), and rotary (RoPE) position embeddings.

Frankly, having a set context length AT ALL doesn't feel great. Speaking from a UX background (and DX to a lesser degree in both senses) in particular: Requiring an exact, preset context length feels like a design decision made with little if any consideration for the user, even if targeting a more technical one. 

max_new_tokens is different. That has actual utility. Other than batch grouping (and I'm not at all convinced that that isn't a self-inflicted limitation either), what's useful about having to chunk, pad, and/or concatenate every single entry of training data?

Recent papers ("The Reversal Curse: LLMs trained on 'A is B' fail to learn 'B is A'" and "Premise Order Matters in Reasoning With Large Language Models") may be indicators that AGI is still further away than the "We're so back!!!" crowd (or the "doomers") want to believe (or want us to believe). I think we have plenty of reasons to temper our anticipation/anxiety, not least of which is that these models are STILL just next <|thing|> predictors.

Personally, these papers serve to bolster my suspicion that positional embeddings, as they exist currently, actively harm generalization (in these cases, context itself rather than context length). While they expose a (perhaps far more obvious) need to rethink data processing, in the - well, context - of PE, these findings seem largely self-inflicted.

It has intuitively made sense to me for a while (since before I was aware of NoPOS, NoPE, etc.) that causal models, in particular, have what they need to figure out enough about where words are (particularly relating to one another) and that PE, in their current flavors, at least, might not add much to - or might even actively harm - length generalization. 

The prevalence of so many (again, admittedly often elegant) modifications to RoPE is a testament to the power of incremental advances... But I daresay that all those interpolation, extrapolation, landmark, beacon, etc. techniques might also be red flags; signs of a deeper problem (no, r/localllama, I haven't tried Ultrapolation yet).

The "no positional embeddings" research is interesting for other reasons than just wanting a 1,524,031-token input with 42 max new tokens (and only setting the latter):
1. It seems (to me, at least) severely underexplored, contrary to the constant drumbeat of PE techniques and modifications. 
2. Not because it's an idea that I had (though in this case, I did; years after some of these papers were published, yet before I was aware of/bothered to Google them, at least), but because it's exactly the kind of "that's just dumb enough to work..." idea that I would have.

The problem with such ideas isn't necessarily that they won't work (I hope). It's that you're going to be hard-pressed to find anything validating your intuition; either because such related work is rare, or because you haven't yet figured out how to search for it. The former is frustrating, but is also a potential opportunity to make an outsize impact in an area that's underexplored and/or taken for granted... Or an opportunity to fail spectacularly at something everyone else already knew didn't work, but never bothered writing down, I suppose; however, even the "writing it down" (ideally with experimental results of its failure) is useful.

Using PE as an example: even if papers like NoPos/NoPE had failed miserably, I would have found them useful. One of the few papers on the subject even reported that non-casual (particularly encoder) models struggled without PE (again, this is intuitive at least to some degree). 

I've got plenty of other dumb ideas. Hopefully, at least a few of them are just dumb enough to work. And even if they fail spectacularly, hopefully, I'll have something to write down (after I wipe the egg off my face). Let's get weird! Stay tuned.
