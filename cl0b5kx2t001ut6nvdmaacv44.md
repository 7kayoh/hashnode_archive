## Roblox games’ servers being attacked!? How?

A few of Roblox games I worked on suffered from an issue where servers randomly gets lagged out. Of course, with no doubts, it’s a vulnerability that exist in their networking infrastructure.

#### The basics

*   Roblox uses RakNet –– A network middleware for multiplayer games
*   RakNet works with both UDP and TCP
*   It has dropped support in around 2014
*   At the time of that, RakNet still has quite a plenty of bugs/flaws remaining unsolved
*   Of course, it is open source under the BSD licence, by Oculus (now Meta? i honestly have no idea about the “renaming”)

#### Introduction

A couple of years ago, I’ve took a look at RakNet’s source code and discovered quite a few vulnerabilities. Such as being able to screw RakNet up, by sending a specifically designed packet string.

At first, I didn’t take it as a serious concern in game development as, I wasn’t working on games back then! And this vulnerability was not “on-trend” in the Roblox community.

Until ~2021, where I finally worked on games and this vulnerability being used to launch attacks on specific games. So! I have decided to revisit this middleware again.

#### Case 1: Using RakNet

I was digging into Roblox’s RakNet infrastructure a few days ago, so don’t really expect me to have strong evidences on each points I’ve made, those are really based on my opinions and assumptions (of course, not 100% opinions)

As what I have mentioned earlier, RakNet contains a lot of bugs and flaws in its code, and the author, Kevin Jenkins, stopped working on RakNet for [a few reasons](http://www.jenkinssoftware.com/). Which also means there are no chance of a patch to resolve all of those bugs and flaws being merged into the code.

Considering the source code is open source in GitHub, exploiters were able to find exploitable flaws and try to abuse it in Roblox.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321932993/FueJn63Iz.png)

A reply made by Quenty to a thread in DevForum

In fact! Quenty has made a post to a thread in DevForum in 2015, which exactly talks about a vulnerability in RakNet.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321934963/SRQqjMCAO.png)

Do excuse the vulgar language used in this image

There is also a “crasher” script which abuses the flaw to screw RakNet up.

#### Case 2: Using custom RakNet

RakNet is open source, that is what I said above, which also means that there’s another possibility –– Roblox created a vulnerability, or they tried to patch the vulnerabilities but didn’t get it right.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321936870/8fwhEZGfB.png)

from zeux.io, a personal website of a Roblox software engineer

It’s clear to tell that Roblox have made changes to the networking infrastructure. Of course, this blog post did not mention a single word regarding RakNet, but the network protocol is heavily related to RakNet.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321939145/JHcfdnJDe.png)

The thread, again! But with zeux’s reply

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321940653/70F002SkU.png)

A reply made by a DevRel regarding this issue, but there is no “update” on it…

From those two replies, and with the image excerpt from a blog post, it’s really likely Roblox has a modified version of RakNet.

Whether has the malformed packet vulnerability been patched by Roblox or not, I do not know. I am not an expert in cyber security (obviously), and I do not have the braveness to risk trying the exploit.

If it has been patched, could it be another vulnerability from RakNet? A vulnerability created by Roblox themselves? Or a new vulnerability pops up after the patch? All those can be possible, but it is uncertain.

#### Case 3: A vulnerability in design

Maybe it can be a vulnerability that exists in most networking middleware?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321942011/xRrQSvfSW.png)

A video in the cloud, name is blurred for multiple good reasons

There is a “DDoS” panel that works for both Roblox and FiveM, and even Tom Clancy’s Rainbow Six Siege.

We know Roblox uses RakNet, but neither FiveM nor R6 does. FiveM uses ENet. And R6 got called out for using a “horribly-made” custom networking library, and got suggested RakNet as well as other libraries, apparently.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321943781/_z70GT68_.png)

Heck, even works for Call of Duty: Modern Warfare

Obviously, this is a really extreme and uncommon case. The panel might have just supported multiple games with different exploits. Which seemed to make more sense, otherwise the whole game industry would be in nightmare already.

#### Other cases

*   “Your game is backdoor’d/has serversides/etc” –– Unlikely, it’s too hard to believe that, when there are multiple games suffering from the same issue, from small to big, from infamous to famous.
*   **“They are just spamming the server IP” –– Does make sense, but spamming the server IP seemed to be really inefficient, still will consider this as a feasible case**
*   “They are just spamming your remotes” –– Again, not when there are multiple games suffering from the same issue, also there are rate limits on remotes
*   You name it?

#### Conclusion

We still have no idea about the cause of those attacks, but we can safely assume that its either custom RakNet or actual DDoS/DoS.

*   RakNet is open source, I have huge doubts that Roblox never modified it. A person I know, also claims that Roblox has a modified version of RakNet deployed in their infrastructure.
*   You can always overload a server by DDoS/DoS, this might be because there are no mitigation policies set for attacks like this, in Roblox’s servers.

I do not have a lot experience in cybersec, so I won’t be making bold claims in areas I am not familiar with. Please! If I made a mistake in this article, do let me know.

*RakNet is not bad, Roblox is not bad either. I am making this article not only because of games I have worked on, but also because of my curiosity*

This article is originally published as a reply to a thread in DevForum.