---
title: Guess What Everyone Else is Guessing Game
aliases: 
tags:
  - math
draft: false
date: 2024-08-20
created: 2024-08-20T20:55:30+08:00
---
Here's a fun little problem that was presented to me and other students in an introductory game theory course.

Imagine there are a group of people playing a game. Each player has to guess an integer between $1$ and $100$ (inclusive) simultaneously. The winner is determined by whoever is closest to $\frac{2}{3}$ of the average of the sum of numbers chosen by all players.

Which number do you choose?

…
…
…

When my professor showed this problem to us, smiles immediately lit up the lecture theatre. Everyone debated on which strategy to go for, continually trying to outguess one another. I quickly realized this wasn't just some quirky classroom game—it was a microcosm of strategic thinking itself.

Many variants explore this sort of strategic anticipation. The original founder Alain Ledoux asked players to guess up to $1,000,000,000$. Others like the British economist John Maynard Keynes created the *Keynesian beauty contest*, where players had to select the six prettiest faces from a hundred photos. The winners are those who picked the most popular of all the players. That is, the average preference of all those involved. 

I gave the initial problem a quick thought, figured it had to be a small number, and picked lucky $13$ in a google survey my professor created. Once everyone picked their chosen number, we eagerly awaited the winner's announcement the following week.

## What's the best strategy?

As a start, let us set a variable $x$ as the number chosen.

What may first come to mind is that $x$ cannot be $100$, because if everyone decided on $100$, then $\frac{2}{3}$ of the average gives us about $67$. This is the highest possible average that could possibly occur. So, we can conclude:

> If we're being rational, we should not be selecting any $x>67$.

In proper terms, we say that the strategy of choosing $x>67$ is *weakly dominated* by alternative strategies, such as choosing $x=67$[^1].

Now, for my class in particular (one filled with game theory enthusiasts), it may be fair to assume the following:

> *We have the knowledge that others, too, are rational*.

If so, then other players will choose $1\leq x \leq 67$. Thus everyone's chosen number is now restricted to that shorter interval. But notice we can use the same line of reasoning earlier to show that $45<x\leq 67$ does not contain the winning number. Again, if everyone picks the maximum possible number in this new interval, $67$, then our new maximum number becomes $\frac{2}{3}(67)=45$. And so our range of numbers reduces down to $1\leq x < 45$.

We can continually apply this set of assumptions and logic:

> *We have the knowledge that others are rational, who also have the knowledge that others are rational.*

If we know that others know that everyone else is rational, then we know that others know that everyone else is shortening their range of numbers to be within $1\leq x < 45$. And so we get the maximum down from $45$ to $\frac{2}{3}(45)=30$.

Extending and summarising this chain of logic:

| Avoid            | Reason                                                 | Assumption                                                             |
| ---------------- | ------------------------------------------------------ | ---------------------------------------------------------------------- |
| ${} x> 67$       | Weakly dominated by choosing $67$                      | $R$: Rationality                                                       |
| $45<x\leq 67$    | Weakly dominated by $45$, assuming others avoid $x>67$ | $R+K(R)$: Rationality + Knowledge that others are rational             |
| $30 < x \leq 45$ | Weakly dominated by $30$, assuming others avoid $x>45$ | $R + K(R) + K(K(R))$: Rationality + 2nd-order knowledge of rationality |
| $20 < x \leq 30$ | Weakly dominated by $20$, assuming others avoid $x>30$ | $R+K(R) + K(K(R)) + K^3(R)$: Rationality + 3rd-order knowledge         |
| $\vdots$         | $\vdots$                                               | $\vdots$                                                               |
| $x=1$            | Survives all eliminations                              | Common knowledge of rationality                                        |

## Common knowledge and the Nash equilibrium

The assumption we're led to, at the end of the table above, is what we call *common knowledge*.

> [!definition]+ Common Knowledge
> A fact is common knowledge (among the players), if for any finite chain of players $i_{1},\dots,i_{k}$, it is true that $i_{1}$ knows that $i_{2}$ knows that $i_{3}$ knows that … $i_{k-1}$ knows that $i_{k}$ knows the fact.

As we may come to expect, if the same group of rational players played this game consistently and assumed a common knowledge of rationality, then through an *iterated elimination of weakly dominated strategies*, the highest possible rational answer gets us down to … pretty much $1$. 

Should all players decide to play $x=1$, under the common knowledge of rationality, we have what we call the *Nash equilibrium* of this game.

> [!definition]+ Nash Equilibrium
> Any combination of strategies in which each player's strategy is their best choice, given the other players' choices.

Any higher guess can be undercut by anticipating that others will reason similarly, and so the only stable outcome is the lowest possible number.

## Back to the real world

Clearly we're not all that rational. While this exact strategy/concept was only introduced to us after playing the game, it didn't make much sense to me at the time to pick $1$, and so I just guessed $13$ at random.

In the end, the average number in my class turned out to be $26.23$, so the winning number was $\frac{2}{3}(26.23)\approx 17$. Unfortunately for me, someone else came closest to that number and won.

### Behavioral insights

With this newfound knowledge and higher-ordered beliefs about others' beliefs, what do you think happens when we play this game out a few more rounds?

Our professor tried this with us again lecture after lecture. As the games progressed, notice how our guesses began to converge downwards. Each game appeared to serve as a feedback loop, where players are adjusting their guesses based on the previous average, anticipating that others would do the same.

![[Pasted image 20250815014420.png]]

What's fascinating is that even without formal instruction, we began to internalize the logic. Rationality wasn't just taught—it's discovered, iteratively, through experience. Indeed, in the same 2005 public experiment with $19196$ participants, the average guess declined over time as well[^2]. Recursive reasoning may very well be a general cognitive pattern.

So, theory shows the game collapses to a single rational choice. Pure reason, when universally applied, leads to predictability. But there's always an intricate dance and struggle between *reason* and the *passions*. Our minds are often influenced by various emotions and biases. Not even economic students, for example, can make the winning guess[^3]. But perhaps it's precisely this tension between the two—our ability to surprise ourselves and defy statistical expectations—that makes life so fascinating.

![[Pasted image 20250817133038.png]]
[^4]

[^1]: This is not a case of *strong* domination, since no single strategy strictly outperforms $x>67$ in *every* possible scenario.
[^2]: Schou, A. (2005). _Gæt-et-tal konkurrence afslører at vi er irrationelle_. Politiken - Den levende avis. [https://politiken.dk/danmark/oekonomi/art5698526/G%C3%A6t-et-tal-konkurrence-afsl%C3%B8rer-at-vi-er-irrationelle](https://politiken.dk/danmark/oekonomi/art5698526/G%C3%A6t-et-tal-konkurrence-afsl%C3%B8rer-at-vi-er-irrationelle).
[^3]: Nagel, R. (1995). Unraveling in Guessing Games: An Experimental Study. _The American Economic Review_, _85_(5), 1313–1326. [https://www.jstor.org/stable/2950991](https://www.jstor.org/stable/2950991).
[^4]: The same game that our professor did with a previous batch of students. Perhaps there was a some collusion going on? (e.g. a group of students selecting 100 on purpose). See [Class broke the guessing 2/3 of the average game : r/math](https://www.reddit.com/r/math/comments/jjfif4/class_broke_the_guessing_23_of_the_average_game/).