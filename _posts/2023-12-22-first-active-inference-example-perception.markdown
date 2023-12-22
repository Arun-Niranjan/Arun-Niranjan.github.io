---
layout: post
title:  "The first recipe in the pymdp-cookbook"
date:   2023-12-22 12:00:00 +0000
categories: active inference
---

## Motivation

This post is aimed at people who are interested in [Active Inference](https://en.wikipedia.org/wiki/Free_energy_principle) and are struggling to get their heads around it (which includes me!).

Active Inference is fascinating but can be really tough to understand. It's very easy to get bogged down in the maths, surprised by MATLAB code and overall get confused. One of the common barriers to entry I've seen (and felt myself!) is where to start in trying to set up a generative model. Lots of tensors start flying around, opaque equations and big words. Oof.

There are lots of tutorials out there for using active inference as a whole. However, I often find the examples are tricky to follow or they assume a lot of prior knowledge. It's intimidating for sure! Just looking things up online is probably not the best way to go. For myself, I'm working through this [textbook](https://doi.org/10.7551/mitpress/12441.001.0001) by Thomas Parr alongside my trusty copy of [Mathematical Methods for Physics and Engineering](https://doi.org/10.1017/CBO9780511810763) when the maths starts to hurt.

I'm hoping these examples will help demonstrate the building blocks that go into specifying a generative model, and I'll try and link them to real world applications as much as I can. I will also comment them in _excruciating_ detail, and do my best to keep the language as simple as possible (but no simpler). What I'm *not* going to do for now is go into the FEP itself - I'll leave that to the proper experts.

They are all based on the [pymdp](https://github.com/infer-actively/pymdp) library, but I'm adding them to a separate repository to keep things decoupled, so I can add recipes as I understand them better, and potentially link to other applications as I build them on top of `pymdp`. Go to the [pymdp-cookbook](https://github.com/Arun-Niranjan/pymdp-cookbook) repository to see recipes as I add them.

## Perception

This is the [first recipe](https://github.com/Arun-Niranjan/pymdp-cookbook/blob/main/examples/perception.py) for a generative model, demonstrating perception.

To perform perception in Active Inference, we still need a generative model. To put it simply, we can't observe everything we care about. Sometimes we have to observe something else that we think (hope!) is _caused_ by the thing we care about. Then, when we observe the related thing, we *infer* what the thing we care about was.

The classic example of this is a clinical diagnostic test, which is often used to explain Bayes theorem. There are plenty of explanations of this in textbooks, online etc. A brief summary here goes like this:
- a person can either have a disease, or not
- we can't know for sure if they have the disease, but we do have a clinical test for it
- the test isn't 100% accurate, it has a "False Positive Rate" and a "False Negative Rate"
- the disease is rare, most people don't have it

And the question we want to answer is:

"If I test positive for the disease, what's the probability I am sick?"

Now the thing to bear in mind here is that you don't *need* Active Inference to solve this problem. You can turn the handle on exact Bayesian inference to get a posterior probability that a person has a disease *given* the base rate of disease in the population (the prior) *and* whether they test positive (the data).

But we can answer this question using Active Inference and the Free Energy Principle, by specifying one of the most simple generative models possible. Later on we can extend the model to solve trickier problems that we can't use exact inference for.

To see this model in detail in a runnable example with lots of comments explaining the setup, go to [perception.py](https://github.com/Arun-Niranjan/pymdp-cookbook/blob/main/examples/perception.py) in the cookbook repository.

As I add more examples, one of my aims is to make them more accessible - perhaps viewable in a browser with no code required. I'll see how it goes.

Thanks for reading!



