---
title: Guess 2/3 of the Average Game
aliases: 
tags:
  - math
draft: false
date: 2024-08-20
---
Suppose there are $n$ people playing a game. Each player has to guess an integer between $1$ and $100$ (inclusive) simultaneously. The winner is determined by whoever is closest to $\frac{2}{3}$ of the average of numbers chosen by all players.


> **Which number should you choose?**


There are many variants to this. The original founder Alain Ledoux used a wider range up to $1,000,000,000$. Others like John Maynard Keynes created a similar guessing game called the *Keynesian beauty contest*, where players had to select the six prettiest faces from a hundred photos. The winners are those who picked the most popular of all the players—i.e., the average preference of all those involved.

The initial version above was introduced in one of my game theory courses, which made for an intriguing session. Smiles lit up the lecture theatre while everyone debated which strategy they wanted to go for. I gave it a quick thought, figured it had to be a small number, and picked lucky $13$ in the google survey that my professor had created. Once everyone finished choosing theirs, we eagerly awaited the winner's announcement in our next lecture.

## Analysis

Let the number we choose be a variable $x$. What may first come to mind is that $x=100$ should not be chosen since if everyone had decided on $100$, then $\frac{2}{3}$ of the average will give us about $67$. This becomes the highest possible average that could possibly occur. As such, we should not be selecting any $x>67$, if we're being **rational**, that is. (In proper terms, we'd say that the strategy of choosing a number above 67 is *weakly dominated* by the strategy of choosing the number 67 itself).

It may seem trivial to assume we're rational. But as my professor had remarked in the following week's lecture: "I have the results with me, but do you guys think there were any of you who actually picked a number above 67?" Immediately, several heads bowed down, guiltily acknowledging their own irrationality.

Now suppose we made another assumption: 

> *We have the knowledge that others, too, are rational*.

If so, then their range of numbers will also be $1\leq x \leq 67$. But by eliminating those $x>67$, we too can use the same line of reasoning in our earlier analysis and claim that no *rational* player would choose $45<x\leq 67$, where $45=\frac{2}{3}(67)$ is now our new maximum.

We can continually apply this logic, getting the maximum down from $45$ to $\frac{2}{3}(45)=30$. Note however that this assumes that

> *We have the knowledge that others are rational, who also have the knowledge that others are rational.*

If other rational players have the knowledge that other players are rational, then we can expect them to shorten the set of possible answers to $1\leq x \leq 30$. This same process can go on and on. Summarizing, we have:

| Avoid            | Reason                                                                | Assumption                                                                                                           |
| ---------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| $> 67$           | Weakly dominated by 67                                                | rationality                                                                                                          |
| $67 \geq x > 45$ | Weakly dominated by 45 once we eliminate 68 to 100 "in others' shoes" | rationality + knowledge that others are rational                                                                     |
| $45\geq x > 30$  | "in others' shoes," "in others' shoes"                                | rationality + knowledge that others are rational + knowledge that others have the knowledge that others are rational |
| $30\geq x > 20$  | "in shoes," "in shoes," "in shoes"                                    | $R, KR, KKR, KKKR$                                                                                                   |
| $\vdots$         | $\vdots$                                                              | $\vdots$                                                                                                             |
| 1                | "in shoes," … "in shoes"                                              | common knowledge                                                                                                     |

As we may come to expect, if the same group of players played this game consistently, then the highest possible rational answer gets us down to…pretty much $1$, given the set of assumptions we've made.

As Keynes wrote about his beauty contest variant of this guessing game:

> It is not a case of choosing those [faces] that, to the best of one's judgment, are really the prettiest, nor even those that average opinion genuinely thinks the prettiest. We have reached the third degree where we devote our intelligences to anticipating what average opinion expects the average opinion to be. And there are some, I believe, who practice the fourth, fifth and higher degrees[^1].

## Common Knowledge

We're not all that rational of course. While this exact strategy/concept was only introduced to us after playing the game, it didn't make much sense to me at the time to pick $1$, and so I just guessed $13$. 

In the end, the average number turned out to be $26$, so the winning number was about $\frac{2}{3}(26)\approx 17$. Only two people came closest to that number, excluding me. Close enough, I suppose.

As a final note, the set of assumptions we made towards the end there is what we call *common knowledge*.

> [!definition]+ Common Knowledge
> A fact is common knowledge (among the players), if for any finite chain of players $i_{1},\dots,i_{k}$ it is true that $i_{1}$ knows that $i_{2}$ knows that $i_{3}$ knows that … $i_{k-1}$ knows that $i_{k}$ knows the fact.

The common knowledge of the rationality of all players explain why the winning guess in our game is $1$. It highlights the need to consider what others will do, for this particular strategy to be played. And that may very well mean expecting others to be irrational, and therefore expect a number greater than $1$, as my own professor had shown.

I think this also serves as a classic demonstration of the intricate dance and struggle between *reason* and the *passions*. While we strive for logical consistency and rational thinking, our minds are also influenced by various emotions and biases. Not even economic students, for example, can make the winning guess[^2]. But perhaps it's precisely our occasional irrationality—our ability to surprise ourselves and defy statistical expectations—that makes life so fascinating.

[^1]: Keynes, J. M. (1936). _The General Theory of Employment, Interest and Money_. Wirtschaft u. Finanzen.
[^2]: Nagel, R. (1995). Unraveling in Guessing Games: An Experimental Study. _The American Economic Review_, _85_(5), 1313–1326. [https://www.jstor.org/stable/2950991](https://www.jstor.org/stable/2950991).