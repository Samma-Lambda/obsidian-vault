Since this week we were allowed to use level 2 on the AI scale, I asked ChatGPT for some ideas of topics to write about for a data ethics deep dive. It gave me a list of eight possible topics, and I asked it to expand on one that sounded interesting: differential privacy.

I ended up choosing differential privacy because it seemed both mathematically interesting and relevant to the kinds of things we talk about in this course. The main idea is that you add noise to a dataset so that the individuals in the data can’t be identified.

Of course, there are limits to how much noise you can add before the data becomes useless. For example, imagine we have data that only takes the values 0 or 1, and we flip each bit with probability 50%. At that point we’ve basically removed all information from the data. If we always flipped the bit, we could just take the opposite and recover the true value. If we never flipped it, we could just read the data directly. But if we randomly flip half of the bits, then we really have no idea what the original value was.

So there is clearly a tradeoff between the amount of noise added and how useful the data still is (even though technically making the data completely unreadable would give perfect privacy). Because of this, differential privacy tries to define a more careful way to think about the problem.

One way to look at it is through queries on the data. Suppose we apply some function to the dataset, like computing the average. The sensitivity of that query is basically how much the output could change if we changed one observation in the data. The amount of noise that gets added is related to that sensitivity. Intuitively this makes sense because the noise is masking the effect of individual observations.

You might wonder why this actually protects people’s data. Without noise, if someone knew the average of a dataset with a certain person included and also knew the average without that person, they could recover that person’s exact value. But once noise is added, there’s enough randomness that you can’t reliably figure out the missing value anymore.

There’s a lot more math behind this, but honestly it feels like something that belongs more in a math or statistics class. The basic idea is that companies can release useful datasets to researchers without exposing individual people, as long as they add the right amount of noise. Since the privacy level is directly tied to how much noise gets added, data leaks become much harder to justify. Situations like the Netflix dataset release that exposed user information could probably have been avoided if techniques like this had been used.

https://medium.com/@RocketMeUpCybersecurity/a-comprehensive-guide-to-differential-privacy-in-big-data-methods-and-prospects-dd659eeb0e5c
https://en.wikipedia.org/wiki/Differential_privacy?utm_source=chatgpt.com#Definition
https://firewalltimes.com/netflix-data-breach-timeline/
