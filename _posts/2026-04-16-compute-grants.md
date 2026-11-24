---
layout: post
title: "How to apply for and get compute grants (for students)"
description: "A practical guide for students seeking GPU compute through HPC allocations and cloud-credit programs."
---


Every PhD student has complained about compute sometime in their lives. At this point, it's the academic equivalent of complaining about not having enough time -- treated as an immutable fact of life, rather than a problem that could actually feasibly be solved. Unlike time however, compute exists in (relative) abundance, if one is willing to look for it. 

In the past year or so, some friends and I have been applying for compute grants for various projects. Altogether, with around 2-3 weeks of effort across our grants, we have accumulated 100k+ GPU hours (as exchanged for A100s), which is roughly equivalent to having a single 8-GPU node running uninterrupted for 2.5 years. Of course, you can divide this if you plan on doing multi-node training or running many experiments simultaneously, but it's not bad for writing a few pitches. 

Surprisingly, I don't think many students consider this as an option, but it's actually pretty simple. I also don't consider myself a particularly persuasive writer (I almost never convince reviewers to raise their scores during rebuttal despite my best efforts, to give you some idea), so I think this process is probably replicable and will give a high return on investment to most people who are willing to put in the work. If you're still reading this, you're probably somewhat sold on the idea of writing compute grants, so let's get into the details:

## Types of grants

There are generally two types of grants:

1. **HPC allocations** - hours on shared supercomputing clusters

2. **Cloud credits** - dollar-value credits on commercial providers such as AWS or Azure

Of these two, I generally think that **HPC allocations** are more worth pursuing, with a caveat. This is because cloud credits evaporate quickly at commercial GPU rates, whereas HPC allocations typically translate to far more actual compute for equivalent writing effort. However, the one caveat is that for HPC allocations, you will be on shared infrastructure, so in other words subject to queue times and generally more affected by the state of the cluster. Personally, I don't mind waiting that much given that CMU already has a large shared cluster, but if you need experiments done ASAP for a deadline, it may be good to have some credits on hand for emergencies.

## Recommended grants

Bracketed labels indicate the applicant country or region, rather than the provider's headquarters. International programmes may still restrict eligible countries.

### HPC Allocations

**Note**: For the US programmes below, international students at US institutions can also apply (I am an international student). International collaborators are also allowed as far as I can tell, as long as the submitter is at a US institution. For all programmes, check the institutional and project-lead requirements; students may need a supervisor to apply.

- **[US] [NSF ACCESS](https://allocations.access-ci.org/)** ⭐ — I consider this to be the best place to start and most worth it for PhD students.
  There are four tiers of increasing scale and effort: 
  - Explore (no proposal, fastest) 
  - Discover (1 page proposal) 
  - Accelerate (3 page proposal, panel review)
  - Maximize (10 page proposal, panel review) 
  
  The PI for Accelerate and Maximize proposals must be post-PhD (at least a postdoc), whereas grad students can be the main PI on Explore and Discover grants. Of the available compute clusters, I recommend **NCSA Delta/DeltaAI**, which has a mix 
  of A100, H100, and H200 nodes.

- **[US] [NAIRR Pilot](https://nairrpilot.org/)** — NSF-backed, AI-focused counterpart to ACCESS. Requires a 3-page proposal; grad students eligible with advisor letter. Also has a lighter Start-Up track (2-week turnaround) good for getting started.

- **[Europe] [EuroHPC AI for Science](https://www.eurohpc-ju.europa.eu/eurohpc-ju-call-proposals-ai-science-and-collaborative-eu-projects_en)** — Compute allocations for AI-based scientific research, including work on foundation models and LLMs. Proposals undergo technical and expert review; allocations last six months. This is the academic route, separate from the AI Factories industrial access modes.

- **[Europe] [LUMI](https://lumi-supercomputer.eu/get-started/)** — Offers both national allocations for researchers affiliated with institutions in LUMI consortium countries and a broader EuroHPC route. The access guide directs you to the relevant country or European call.

- **[UK] [AI Research Resource (AIRR) Gateway](https://www.ukri.org/opportunity/access-to-isambard-ai-and-zenith-airr-supercomputers-gateway-route/)** — Up to 10,000 GPU hours over three months for smaller AI projects, testing and benchmarking. Open to UK-based researchers at eligible organisations; the project lead needs an employment contract covering more than the project duration.

- **[France] [Jean Zay / GENCI](https://www.edari.fr/)** — Apply through eDARI for compute and storage allocations. Applicants must belong to or be associated with a French research institution, publish their research and submit an activity report.

- **[Spain / Europe] [Spanish Supercomputing Network (RES)](https://www.res.es/en/services/access-and-calls)** — Shared HPC and AI resources for researchers at Spanish and European institutions. Check the standard and fast-track access routes; fast-track has additional grant requirements.

### Cloud Credits

- **[International] [Nvidia Academic Grant](https://www.nvidia.com/en-us/industries/higher-education-research/academic-grant-program/)** ⭐
  — Proposal-based, and not always open (check if there is a call for proposals). Requires a faculty PI, but PhD students can be involved. Unlike most cloud credits, this gives GPU hours on Nvidia cloud infra (e.g. use of an 8xA100 node for 6 months).

- **[International] [Lambda Labs](https://lambdalabs.com/research)** — This is a very straightforward application, the credit amounts seem to be lower (e.g. ~2k) but it's very low friction to apply.

- **[International] [Google TPU Research Cloud](https://sites.research.google/trc/about/)** — Access to TPUs for ML research. Best fit if your stack is JAX/PyTorch XLA.

- **[Selected countries] [Google Cloud Research Credits](https://edu.google.com/programs/credits/research/)**
  — Note that this is separate from the above. This has rolling applications and low friction; see the [eligible countries](https://support.google.com/google-cloud-higher-ed/answer/10324705). Up to 5k for faculty/postdocs, 1k for PhD students. Covers GPUs and TPUs on GCP.

- **[International] [AWS Research Credits](https://aws.amazon.com/government-education/research-and-technical-computing/cloud-credit-for-research/)**
— Application-based cloud credits. More involved process than Lambda.

- **[Country eligibility not specified] [Microsoft Azure Research Credits](https://www.microsoft.com/en-us/azure-academic-research/)**
  — Similar to AWS/GCP credits, proof-of-concept focused. Also contributes 
  resources through NAIRR so there's some overlap if you're applying there too. **NOTE: the form may be closed if you don't see anything on this page.**


## How to apply

The application process is slightly different for each grant, so you should probably read the instructions carefully if you plan on applying for one. One thing is that you should probably come up with a project first and have some potential collaborators ready, since you need to write a proposal and detail the preparedness of your team. This tends to be easier to do if you already have a pretty good idea of what you want to do, and also a team. Some grants require a faculty member or postdoc to submit them, so you should probably try to get one on your team.

A useful framework for structuring your proposal is the 
[Heilmeier Catechism](https://www.darpa.mil/work-with-us/heilmeier-catechism), a set of questions that any good research proposal should be able to answer. It's worth going through before you start writing.

Finally, the best thing you can do before writing is to find a past accepted proposal for the grant you're targeting. Most programs have examples floating around if you ask around or search a bit, and they give you a much clearer sense of what to write about and can serve as good templates.

**Update (November 2026):** Added European compute opportunities in the list. Thanks to Marc Winn for suggesting these resources! His [ComputeFinder directory](https://computefinder.net/free-compute) lists more non-US options.
