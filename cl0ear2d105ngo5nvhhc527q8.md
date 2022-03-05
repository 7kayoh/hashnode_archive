## V5: Recode & Recode & Recode

Last year, we released V5, and then shut it down because of the bugs in it. Everything in development was going well. In fact, we did conduct tests on V5 to test out the performance and the UI, et cetera. Not until when we decided to release V5 –– UI no longer work for no reason, poor gameplay performance, and even, backdoors.

The whole team (including the leadership team) felt in awkward, not the fact we got backdoor'd in V5, but the fact that we shipped a game that is **really terrible**.

So, what did we learn and what do we plan to do next?

___

## Background

I am a Roblox game developer, of course. Just check my articles, they are pretty much all about Roblox development. I happen to work in a group called Frappé, employed as a developer working for the upcoming version V5 at 25/04/2020.

Development of V5 started in around 2017-2018, but it eventually got restarted due to some issues. Enters the re-V5, which is the current V5.

The UI was done, but there are a few missing parts in it. Some critical features were missing because the previous UI designer left. So I was employed to finish those missing parts and as well as finish some part of the backend.

We had a really tight deadline when I was employed to work on it. I think we had only 3-4 months left before shipping it to the public, so we have to rush finishing most of the part (horrible idea). Therefore, this leads to low-quality code and introduces a lot of bugs in the game that still remains unfixed when the game launches. V5 also uses some of the code in previous version, and previous version is a combination of code in older version and new code, which makes it a lot worse because consistency between code is lost.

We tested the game multiple times before actually releasing it, but we did not do any sort of stress-tests, which means the capability of the backend is unmeasured and is likely to be vulnerable to large player base considering it is rushed.

## The problem

Okay, it's August in the same year, we released V5 to the general public. It was full of hype. The fact people waited so many years for V5 to come out, makes V5 a trending topic in the group RP category. Which also means that the player base is increased by a lot more than what we were expecting.

Initially, many acknowledged FPS drops while playing the game, most people got an average FPS of 20-30 in V5 –– not something we are expecting to happen. Then, bugs in the backend made a lot of functionalities go malfunction. The gameplay experience is affected **by a lot**, in fact, nothing really works in the game. We were alerted by this issue and we were completely shocked. The problem is so severe that it creates a lot of negative feedback regarding the group, and still is not completely relieved to this day.

## What we learnt

We eventually closed down the game and rolled back to V4 and announced that we will be optimising the game and will be rereleased shortly this year. This promise was made but never satisfied, and I believe the reason why is...

- There are too many bugs, we simply can not afford the time to fix all the bugs completely
- The whole codebase structure is flawed
- Error handling is improperly done, especially in remotes
- Heck, the performance is so bad that we can barely work on it in Studio
- Backdoors!!! It's too painful to get rid of them

So, what have we done to prevent any of those issues above, for the future?

- Newer projects are coded with a MVC framework called [Knit](https://github.com/Sleitnick/Knit)
  - We have now established a standard codebase structure for our games' code
  - Knit is Single-Script Architecture, modules run in sync and conflicts are less likely to occur
  - Code quality is ensured to be high
  - It is much intuitive for developers to work with

- Error-prone code is now wrapped in `rpcalls` (recursive pcalls), such as code interacting with Http APIs, et cetera

- Errors are properly handled with the help of promises
  - An error may not mean that code will be unavailable, we can consider using an alternative solution

- Errors are logged to our log drain (Self-hosted Sentry)
  - More easier for us to do debugging

- Newer projects are done with Rojo and done in a Git repository
  - Small patches, UI etc does not require opening Studio to finish, reducing the load time and developers can work on games with a lower-end device or tablets
  - Established a new developer policy in the coding department
    - Developers only have **read** access to projects they are assigned to. To publish their changes, they have to create a new pull request and ask for reviews from the head developers. Reducing the probable chance of backdoors
    - Only head developers have **maintain** access
    - 2-factor authentication is required
  - Coding can be done with a code editor, reduces the memory overhead compared to using Roblox Studio

- UI is now written with a declarative UI library called [Fusion](https://github.com/Elttob/Fusion)
  - Increases the readability and maintainability of the code
  - Components reduces duplicated code
  - States make race conditions less likely to occur

- And a lot more

## What to do next

With all the changes above, we definitely can not work on the current V5 anymore. The current V5 is not done with Knit, nor is in Git, nor its UI written in Fusion either. So, we decided to recode it from scratch, completely. Start with an empty project.

Of course, this means that folks will be waiting a lot more time for a complete rerelease of V5 to come out. But what you are getting is: **high-standard**, **high-quality**, and **performant** code in the game. Juicing every single part of your hardware to give you the most immersive, most stable and smoothest gameplay experience possible.

![](https://cleanshot-cloud-fra.s3.eu-central-1.amazonaws.com/media/28981/NQSco0KJtxfaWKDKHaTxXDBpJfjAt7C79YySkZFQ.jpeg?X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEBMaDGV1LWNlbnRyYWwtMSJHMEUCIFT26%2B9S0JDzPti6JAJWXtCGKfbe434PPgr%2FTideE2NRAiEApL7RzN4C%2FHHh4Kq%2FYtMhlLoww%2BpsGoPKLu%2Foh91wq6oqoQIIfBAAGgw5MTk1MTQ0OTE2NzQiDF1sKz5flQzNYGKT7Sr%2BARyoyHzX1hyFbgkMkaO58fhQJqbSTxrJZkVA%2BXIgkOOtK%2B6PMr%2FO8ioRSdlyK6e1pPhrlTp%2FB1BtQZIJXyMlKMkDeN1VUB%2B1kcJAj84xPBcM7iDHSLlJCyhrg1NwsU2DULf4%2FfIKUB73WVWxIL0gOiMQfHaQEGK27VSlTjUfpm9Unz28Qf7QHS5jvn9uk2s%2F8nYim7tQnsIBaKZj9LM87QW%2BvjWxSA6azDWdXlqQto4R81wwLDg0743SMPXUycLhX0M277sLtYe%2FQpdPxyK7KD%2BWsDJo9RMbtEZlJpQ0Y9d%2Fjfeh%2FL3re5xOfvbNi%2B6LKBZGS7NcfL8VWKWB06YtMPbrjpEGOpoBzTAWxP0NF9z%2FqEfUfWWjTr4uEAIgAV7vs2MrU6FRwDGW8D7PkmlEZ1vK8m6QdESVhvzmRJbQaglrMGPb0O9s4ivYPh2gKyPH3RURh4SHG8o3CSzwu5LdlYdJ4A%2Fbt75iWm1V5RHnpkOWd%2F41dqQ7YeTanmwJHo7zRFipUdw9NE1aQptwVH6TgL4PFnhnmZhpi0AmLzAxUXZnVA%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIA5MF2VVMNKYEL6OMY%2F20220305%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20220305T202412Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Signature=e9faf906e8f794f39f5a3a4be482e7f656f308ce1fb4a6467656c03ad8b44759)

We have already began working on it, and it's going really well. Our developers prefer coding in this environment compared to the traditional one in V5 and others.