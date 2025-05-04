---
layout: post
title: The Promises and Pitfalls of AI Scientists
---

Recently, I saw news that an AI-agent generated [paper](https://sakana.ai/ai-scientist/) was accepted to an ICLR workshop. I've been interested in this topic for a while, and some masters students I'm working with are currently building a benchmark for end-to-end scientific reasoning in LMs (from idea generation to coding/execution), so I was curious to read the paper. I'm not actually skeptical that LM-based agents can eventually automate parts of research or serve as assistants in many aspects of research. In fact, I often ask LLMs to fetch literature related to research ideas, draw plots, critique ideas, and more. If you haven't tried this yet, you should! Sometimes it's not very helpful, but the LMs tend to call every idea you pitch brilliant and innovative, which is very good for building confidence (NOTE: this is not referring to gpt-4o's recent update, which verges into sycophantic). I explain this to say that I wasn't looking for flaws at all, and was rather thinking about how this particular system could be benchmarked.

The issue is: the paper is completely terrible. It's actually quite impressive how bad it is given the strict page limit, as it manages to be bad in multiple different and conflicting ways even within 5 pages. This is the type of paper I wish I got more of as a reviewer -- in the sense that it's more fun to write 1-star or 5-star ratings compared to 3-star ratings. I've attached the annotated version to this post, but I'll just review a few of the major problems here:


### Critiquing the paper (or: the fastest review I've ever written)

Attached is a PDF of comments: I review papers in exactly the same way (though I spend much more time and leave more comments for real papers). The comments in red are from Sakana AI, while the little speech bubbles (mouseover) are my comments.

<div style="width:100%;height:600px;border:1px solid #ccc;margin:1em 0;">
  <iframe
    src="{{ '/assets/papers/ai_scientist_paper_review.pdf' | relative_url }}"
    width="100%" height="100%">
  </iframe>
</div>

You can read through the remainder of my comments, but the core idea itself just basically doesn't make sense. The idea is to encourage compositional reasoning in language models (LSTM in this case) by using the following penalty, where $T$ is the sequence length and $h_t$ is the hidden state at time $t$:

$$ L_{\text{comp}} = \frac{1}{T - 1} \sum_{t=1}^{T - 1} \left\lVert h_{t + 1} - h_{t}\right\rVert^2$$

It is actually unclear if this is the embedding or the hidden state, the paper seems to refer to it pretty clearly as the hidden state but the sakana comment mentions that this is a typo and it should actually be the embeddings referenced in this section. This embedding idea actually makes even less sense so I'll ignore it. If the embedding idea is secretly genius feel free to email me about how it could possibly work, but it honestly destroyed multiple braincells for me to contemplate this idea (I need those! I haven't got many!) so I would prefer not to think about it further.

If you look at that penalty and wonder how it would actually produce compositional reasoning, you would be right...in the "hidden states" interpretation this maybe makes sense in some circumstances: in non-compositional expressions, the hidden state can potentially change a lot in some cases (e.g. in an idiom like 'raining cats and dogs' where the meaning isn't derived from the individual words but requires a sudden shift to the idiomatic interpretation after processing the end of this text chunk). If we enforce that the hidden state shouldn't change a lot, it would prevent these types of sudden shifts after reading tokens. However, this in itself does not promote compositional reasoning. It's pretty clear that a constant hidden state would satisfy this, yet this goes against the very essence of compositionality, which is roughly that "an output should be a specified function of the inputs". If you then look at all the other issues in the paper such as figures not matching what the text is claiming, missing references and so on, this really isn't any good.

**Final score**: 2/10. I gave this higher than a 1 because it at least vaguely is in the form of a paper, with an abstract, different sections, some experiments, and a figure or two. 

## So how did this get past review?

Finally, I'd like to emphasize that this is not a "deep dive" into the paper nor am I nitpicking. These are very obvious flaws that were easy to find -- it took probably 5 min to read up to section 3, being very generous. Sakana's review of the paper oddly focuses on minor details, but there's no need to look at the trees if the forest is burning down so to speak. So the question should be: how did this get through review?

The first answer is: this is a workshop, and those tend to have lower standards. That's true, but ideally workshops shouldn't admit work that's clearly extremely flawed or low-effort either. As a heuristic, the reviewers shouldn't be spending more work reviewing a paper than the authors did writing it, or as a co-chair put it succintly, "you can't just submit any random 5 page document and expect people to spend their valuable time reviewing it". It seems like some organizations (such as those where high schoolers pay to get research experience) are already submitting their papers en masse to workshops, and I hope AI scientist startups or less scrupulous individuals don't also start doing this (cope).

I think a deeper issue is reviewer overload and subsequent low effort reviews. This is hopefully an uncontroversial opinion, but in the NLP/ML community (which I'm familiar with), peer review is extremely stochastic, and you can often scrape by with a bad paper (in this case) if you get three reviewers that just say something like "looks good to me" (without reading the paper), or conversely get rejected if you get three reviewers that nitpick on inconsequential/mistaken points (without reading your rebuttal).

There's no clear solution to this, and I don't see the peer review situation getting better due to the rapidly increasing number of papers submitted each year. Having low acceptance rates and stochasticity in reviewing also incentivizes authors to submit many papers and directly resubmit rejected papers to the next conference deadline until they get accepted, creating an even bigger backlog.

Ironically, LLM reviewers might actually be above average human level, but for the wrong reasons. Not to say that we should just replace reviewers with LLMs either, that would be a bit too dystopian for now.

Until models can actually conduct end-to-end science themselves and trigger [paradigm shifts](https://thomwolf.io/blog/scientific-ai.html), I worry about the spam they'll release on a human audience. Human reviewers are already overloaded with human-written papers, they don't have the capacity to review random 5-10 page documents generated en masse by people just wanting to attach their names to a publication. I've seen similar spam from people using LLMs to generate books, but at least these books aren't forced on readers.

I do think that LMs have a lot of headway to help us in solving scientific problems, and I already use them to help me with many tasks. However, there's definitely going to be a huge adjustment period until then, and scaling up reviewer count and quality (or creating really good AI reviewers before AI scientists) is going to be a major challenge.