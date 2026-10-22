---
title: "Avoiding the Decline to Meat Proxy"
date: 2026-10-19
draft: false
---

Understatement of the decade: AI has had a massive impact on software development. I wanted to make a developer tool that encourages the benefits of productivity of its use without the degradation of skill from outsourcing the developer’s thinking.

The goal with this developer tool is to find the right balance with AI. Not using AI, as a fellow coworker once said, is “leaving productivity on the table”. I agree; however, I think too much use will cause many critical thinking skills to atrophy and create a reliance on the tool you use.

> It frequently forces workers to adapt to the speed and demands of machines, rather than machines being designed to support those who work. As a result, contrary to the advertised benefits of AI, current approaches to technology can paradoxically de-skill workers, subject them to automated surveillance and relegate them to rigid repetitive tasks. The need to keep up with the pace of technology can erode workers’ sense of agency and stifle the innovative abilities they are expected to bring to their work.[^2]

To best draw this line at a high level, is to keep the AI at read only permission. This allows the AI agent to get full context of your building directory without making changes itself. To properly know what you are asking, gather information related to your inquiry, and recommend a solution given the knowledge pushed and trained. By having to run or write yourself you still drive the vehicle.

Driving by entering in commands and writing can be tedious. So what is the case for doing the repetitive and tedious? You actually learn. We are not simply told once and then subsequently lock that information in. We need repetition to strengthen the importance for our neural paths to lock in that lesson.

If you aren’t a software developer but of another domain and just want to get things to work end to end, then vibecoding with documentation, unit tests, and clear criteria works fine. Especially if you have the token budget i.e. a provided enterprise plan. Then go crazy with pipelines and mult-agent work. Sometimes you just need something to work to provide the idea is applicable. This tool isn’t for that purpose. This tool is for maintenance and learning. 

This read only method is already done in Ask mode in most AI agent products, so why build my own?
It is easy to degenerate with a simple push from the user to switch to agent mode. To checkout from work because you are tired or don’t feel like it on a Friday. With laziness this is all too easy.

I know this "all too easy" temptation to succumb to laziness and let the AI just do it. As I have done this very thing while developing this project. I got tired and let the AI agent write the files itself with running the unit tests to verify everything works as expected.

## Why blind AI use is bad

So why is this bad? First of all you will inherently accumulate technical debt. But what if the AI agent documents the change and writes an explicit unit test for it? This helps mitigate but still doesn’t solve the problem of technical debt on your end. If AI can solve the problem you are ok but if not you are now at a point where you have no idea what is really going on under the hood. At this point you have to use a better model or spend a significant amount of time familiarizing yourself with the problem.

Blind AI use provides a short term solution boost with long term painful consequences.

The resistance to the not think workflow could be chalked up to resistance to new disruptive technology. People don’t till the land itself. They transitioned to tools and mules. Now we use John Deere with diesel and a screen. There are several examples of new tools disrupting industry and how people work. Allowing us to spend more time and energy at a higher level where the lower level is handled by our tool. But this is different.

Now the language medium you use for thinking and expressing ideas is done via a machine. The past tools were an extension of the hands where now the tool is an extension of the tongue. There is no way that more use of AI will not end up in atrophy in skills needed for a human being to function properly.

You see coworkers now becoming meat proxies[^3]. Simple copying problems captured in text to solutions provided in texts from AI. PR’s filled with comments of Claude agents talking to themselves. We are more than just a way for AI to interact with the world in ways it is currently unable to. We would turn into tools for the tools we created.

This does not mean we don’t use it. We just need clear hard set boundaries to prevent degradation into domesticating ourselves via the tools we create.

> Precisely in order to avoid this drift, it is necessary to design systems that are centered on the human person and not solely on performance.[^2]

## Keeping humans in the loop

So how do we use AI to enhance our long term productivity without reducing ourselves to copy paste zombies. You use the read only feature to force even if it is tedious write and execute processes to prevent lack of thinking. You also lock it up in a VM. Mirror the directory paths for AI to see a reflection of you work but not the original. Simultaneously leaving out files that should not be seen such as secret keys. There are still vulnerabilities with this as with any software. For those aware I’m sure you are thinking of the Hugging Face Incident.[^1]

The Hugging Face incident is often referred to online as a “warning shot”. This handily plays into OpenAI marketing playbook of hyping their product while emphasizing their technological power and subsequent need for their customers to continue to use them to harness that power for their goals. At worst this is fear mongering, which you can see in full on YouTube thumbnails to drive clicks through fear. Fear of missing out and a grave external threat.

![YouTube result: "AI Just Crossed the Terrifying Line - Now What?" by Kurzgesagt, thumbnail reads "WE LOST CONTROL"](/images/HuggingFace_WarningShot_1.png "Kurzgesagt – In a Nutshell: \"AI Just Crossed the Terrifying Line - Now What?\"")

![YouTube result: "The OpenAI/Hugging Face attack, clearly explained" by Dwarkesh Patel](/images/HuggingFace_WarningShot_2.png "Dwarkesh Patel: \"The OpenAI/Hugging Face attack, clearly explained\"")

![YouTube result: "Hugging Face: Why AI Might Kill Us" by Hoog](/images/HuggingFace_WarningShot_3.png "Hoog: \"Hugging Face: Why AI Might Kill Us\"")

This is no way to completely solve this security problem but that does not mean we shouldn't work hard to mitigate it.

Now that we established the more philosophical and high level problem how do we practically gain the benefits of AI without the atrophy of critical thinking that follows its use.
My practical approach to utilizing the best of AI without the atrophy is for a more human centered design. This starts with clear, hard set boundaries for the AI and by subsequently keeping the user from falling into out sourcing their thinking.

## Readonly

Readonly is a cli tool to wrap ai cli agent in a VM. The only paths shown are specified by the user for the ai agent to see and only allows read access. The VM environment is slim debian base image with QEMU to allow running the VM on any OS. Currently only made and tested on linux (fedora). The OS image was generated in yocto to control the entire config the AI is located in. After installing the image, you call readonly install with following command that is recommended for Linux installs. From then once you specify readonly then ai agent like claude then the directory ex: `readonly claude`. If no directory it assumes the current directory the command is called. Images are snapshot after installation and authentication to prevent reinstalling and re-logging in every run. Also a default mask is used for .env files and directories. Other masking paths can be specified as well. This guarantees access to your code repository to help out but prevents ai agent from reading your private keys. A much stronger protection beyond asking it and hoping it doesn’t read your private keys.

With that said the AI agent still has internet access. This is deliberate as public access is needed in order for frontier models: Claude and OpenAI models to work.
This leaves an opening to major security faults best recently seen from again the Hugging Face Incident but currently I decided to except this risk for the benefit of improved performance over hosting local models.

This more human centered designed is made in hopes of a flourishing of persons rather than erosion. Like with any good relationship clear enforced boundaries set for both human and tool to do what their role requires. With humans in the drivers seat.

I have strong hope that with focusing on the human person growth rather than token consumption, we can have a system that gives short term and long term boosts.

## What's next

In true MVP fashion I built it to work but not much beyond that. To hit the 2 week deadline and to continue moving forward many features were cleaved and this is still very much a work in progress. Also old habits die hard as I really spent more than a month on this, all the more reason to move on. However the baseline objective of keeping AI in a VM with readonly access and masking has been achieved. More work to strengthen the security and user feedback are needed. I’ll be using this tool for future projects to verify its utility and my hypothesis.

I do think there is application for building with AI where not a single line of code is written by the user, but rather fully stating the logic flow and corresponding states enough to capture each feature in visual nodes to be translated to code by AI. This way you still think deeply and fully about the solution (in theory) just without the code. This style attempt will be for another developer tool to create in the future. 

So the next step from telling people about what I built so I don’t build in a cave is to move onto the next rotation. This build was not designed to be a single loop but to be used for the next rounds to be actively developed and verify it’s utility alongside the products I will be building. Looking forward to the next round as I attempt to start the journey of fixing my terrible posture while coding. Another developer tool of sorts but with more hardware.

The projects mentioned here are on GitHub:

- [readonly](https://github.com/stayingcozy/readonly): VM that ensures AI agent CLIs get readonly access and masks `.env`
- [meta-readonly](https://github.com/stayingcozy/meta-readonly): Yocto build for the readonly VM image

[^1]: OpenAI, [“Hugging Face incident and the road ahead”](https://openai.com/index/hugging-face-incident-and-the-road-ahead/).
[^2]: *Magnifica Humanitas*.
[^3]: Hacker News discussion: [news.ycombinator.com/item?id=49151933](https://news.ycombinator.com/item?id=49151933).
