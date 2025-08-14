---
title: Guess 2/3 of the Average Game
aliases: 
tags:
  - math
draft: false
date: 2024-08-20
modified_date: 2025-08-14T23:12:07+08:00
created: 2024-08-20T20:55:30+08:00
---
Here's a fun little problem that was presented to me and other students in an introductory game theory course.

Imagine there are $n$ people playing a game. Each player has to guess an integer between $1$ and $100$ (inclusive) simultaneously. The winner is determined by whoever is closest to $\frac{2}{3}$ of the average of the numbers chosen by all players.

Which number do you choose?

…
…
…

When my professor showed this problem to us, smiles lit up the lecture theatre. Everyone debated on which strategy to go for, continually trying to outguess one another. I quickly realized this wasn't just some quirky classroom game—it was a microcosm of strategic thinking itself.

There are, in fact, many variants that explore this sort of strategic anticipation. The original founder Alain Ledoux used a staggering range of up to $1,000,000,000$ numbers to choose from. Others like the British economist John Maynard Keynes created the *Keynesian beauty contest*, where players had to select the six prettiest faces from a hundred photos. The winners are those who picked the most popular of all the players. That is, the average preference of all those involved. 

I gave the problem a quick thought, figured it had to be a small number, and picked lucky $13$ in the google survey that my professor created. Once everyone picked their chosen number, we eagerly awaited the winner's announcement in our next lecture.

What's the best strategy here?

## Initial analysis

As a start, let us set a variable $x$ as the number we choose.

What may first come to your mind is that $x$ cannot be $100$, because if everyone decided on $100$, then $\frac{2}{3}$ of the average gives us about $67$. This is the highest possible average that could possibly occur. So, we can come to the following conclusion:

> If we're being rational, we should not be selecting any $x>67$.

In proper terms, we say that the strategy of choosing $x>67$ is *weakly dominated* by the strategy of choosing $x=67$.

Now suppose we made another assumption: 

> *We have the knowledge that others, too, are rational*.

This may be a fair assumption to make in my class—one that was filled with game theory enthusiasts. 

If so, then they too will choose $1\leq x \leq 67$. So everyone's chosen number is now restricted to that shorter interval. But notice that we too can use the same line of reasoning earlier and show that $45<x\leq 67$ does not contain the winning number. Again, if everyone picks $67$ (the maximum possible number in this new interval), then the winning number becomes $\frac{2}{3}(67)=45$, our new maximum. And so our range of numbers to choose from gets reduced down to $1\leq x < 45$.

We can continually apply this set of assumptions and logic:

> *We have the knowledge that others are rational, who also have the knowledge that others are rational.

If we know that others know that everyone else is rational, then we know that others know that everyone else is shortening their range of numbers to be within $1\leq x < 45$. And so we get the maximum down from $45$ to $\frac{2}{3}(45)=30$.

Summarising this chain of logic:

| Avoid            | Reason                                                                | Assumption                                                                                                                 |
| ---------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| $> 67$           | Weakly dominated by 67                                                | $R$ationality                                                                                                              |
| $45<x\leq 67$    | Weakly dominated by 45 once we eliminate 68 to 100 "in others' shoes" | $R$ationality + $K$nowledge that others are rational                                                                       |
| $30 < x \leq 45$ | "in others' shoes," "in others' shoes"                                | $R$ationality + $K$nowledge that others are rational + $K$nowledge that others have the knowledge that others are rational |
| $20 < x \leq 30$ | "in shoes," "in shoes," "in shoes"                                    | $R, RK, RKK, RKKK$                                                                                                         |
| $\vdots$         | $\vdots$                                                              | $\vdots$                                                                                                                   |
| 1                | "in shoes," … "in shoes"                                              | Common knowledge                                                                                                           |

## Common knowledge and the Nash equilibrium

The set of assumptions we made towards the end of the table there is what we call *common knowledge*.

> [!definition]+ Common Knowledge
> A fact is common knowledge (among the players), if for any finite chain of players $i_{1},\dots,i_{k}$ it is true that $i_{1}$ knows that $i_{2}$ knows that $i_{3}$ knows that … $i_{k-1}$ knows that $i_{k}$ knows the fact.

As we may come to expect, if the same group of rational players played this game consistently and assumed a common knowledge of rationality, then through an *iterated elimination of weakly dominated strategies*, the highest possible rational answer gets us down to…pretty much $1$. 

We say that the *Nash equilibrium* in this game, under common knowledge of rationality, is for all players to choose $1$.

> [!definition]+ Nash Equilibrium
> Any combination of strategies in which each player's strategy is their best choice, given the other players' choices.

Keynes had this to say about his beauty contest variant of this guessing game:

> It is not a case of choosing those [faces] that, to the best of one's judgment, are really the prettiest, nor even those that average opinion genuinely thinks the prettiest. We have reached the third degree where we devote our intelligences to anticipating what average opinion expects the average opinion to be. And there are some, I believe, who practice the fourth, fifth and higher degrees[^1].

We're not all that rational of course. While this exact strategy/concept was only introduced to us after playing the game, it didn't make much sense to me at the time to pick $1$, and so I just guessed $13$. 

In the end, the average number turned out to be $26$, so the winning number was about $\frac{2}{3}(26)\approx 17$. Someone else came closest to that number (and thus won), although I did come quite close with $13$.

## Real-world implications

If all players are perfectly 

The common knowledge of the rationality of all players explain why the winning guess in our game is $1$. It highlights the need to consider what others will do when implementing this strategy. Paradoxically, that may very well mean expecting others to be irrational, and therefore expect a number greater than $1$, as my own professor had demonstrated.

I think this also serves as a classic demonstration of the intricate dance and struggle between *reason* and the *passions*. While we strive for logical consistency and rational thinking, our minds are also influenced by various emotions and biases. Not even economic students, for example, can make the winning guess[^2]. But perhaps it's precisely our frequent irrationality—our ability to surprise ourselves and defy statistical expectations—that makes life so fascinating.

[^1]: Keynes, J. M. (1936). _The General Theory of Employment, Interest and Money_. Wirtschaft u. Finanzen.
[^2]: Nagel, R. (1995). Unraveling in Guessing Games: An Experimental Study. _The American Economic Review_, _85_(5), 1313–1326. [https://www.jstor.org/stable/2950991](https://www.jstor.org/stable/2950991).