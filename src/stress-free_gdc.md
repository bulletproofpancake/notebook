# [Stress-Free Game Development: Powering Up Your Studio With DevOps](https://youtu.be/t9HRzE7_2Xc)

# Background

- Made CrashLands in 2015
  - Worked on for two years
  - Did a beta test
    - 150 players
    - 2,200 unique bug reports
    - Crunched for 2 months fixing bugs
    - Were not able to fix everything
  
  - Launch
    - 100,000 players
      - New bug report wave
      - Bugs introduced during crunch
      - Crunched to fix bugs instead of working on new content
  
  - Content Updates
    - None of the builds were working
    - Weeks to get builds working again
    - New wave of bug reports
    - Only 2 content patches in a year (a constant, waking nightmare)
  
  - Hired more people
    - Had a hard time integrating people as there were no systems
    - The members were doing so many things that they didn't have the time to create any kind of onboarding structure
    - New members wanted to contribute but unable to
  
  - The art problem
    - The increase in artists meant twice as much art to implement into the game for the solo programmer
    - Left less time for developing game systems
    - Artists got demoralized because assets were not being used

## Art Asset Pipeline
![](https://i.imgur.com/kbMJJfh.png)

- Offloaded the `Import Asset` step from the programmer
  - Solved by the Inkbot
    - Made by another developer in the team which allowed the programmer to mass import the assets from the art team in seconds
    - For it to work, assets had to be standardized, which meant that the export side should also be automated
  - While faster for the programmer to import, it also sped up the artists which ended up with more unused assets
    - Art team became more demoralized and the programmer became more stressed

## 2018

- Company was scaled down
- Previous game being worked on was scrapped due to out-of-control processes
- Started development of LevelHead
  - Similar to the original Mario Maker
  - Development continues like before
  - When the launch was discussed, it was found that LevelHead was getting similar to the launch of CrashLands
    - The game wasn't being actively tested
    - Would probably go through the same motions all over again
    - Learned DevOps through research
    - Applied DevOps principles over the next year and turned the whole ship around

![](https://i.imgur.com/9b0qgFI.png)

# DevOps

![](https://i.imgur.com/sANLeF4.png)

# The Three Ways of DevOps

## Managing the Flow of Work

![](https://i.imgur.com/QtnQIkk.png)

### Eliminating Waste

#### Waste
  - Anything you do that isn't delivering value to your customer.
  - Always worse than you think
  - Creates more waste and is self-perpetuating

#### The Circle of Waste
##### Motion
- Waste produced by movement of materials or information
- Sending multiple emails to communicate and still having a meeting
- Introduces a lot of [waiting](#waiting) and [task switching](#task-switching)
- Create self-service systems such as good documentation so that information is always available rather than waiting for somebody else for the information

##### Task Switching
- Waste produced by the expense of changing between contexts
  - Meeting -> Production -> Meeting -> Lunch -> Work -> Meeting
  - Causes [waiting](#waiting) and [defects](#defects)
  - Can be minimized by batching work by type
    - Save meetings at the end of the day
    - Check emails in bursts instead of constantly

##### Defects
- When something isn't usable by the people downstream from you
  - Assets in the wrong size, sound in the wrong format, etc
  - Creates the following waste:
    - [motion](#motion) because the person encountering the defect has to stop working and return it to be fixed
    - [task switching](#task-switching) because the previous developer planned on doing one thing and is now fixing errors
    - The person now has an [unfinished projects](#unfinished-projects) because they are [waiting](#waiting) for the problem to be resolved
    - If a defect makes its way to a player, the developers would have to engage in [heroics](#heroics) like pulling all-nighters to deploy a hotfix
  - To cut down defects, fix the processes that create them in the first place

##### Waiting
- When something is supposed to happen, but it doesn't
- Waiting gives the person a tendency to not start working because something else might arrive at any moment which would cause a [task switch](#task-switching) and lead to an [unfinished project](#unfinished-projects)
- To reduce waiting, deliver work continuously in small batches

##### Unfinished Projects
- A project that work has stopped on for an extended period of time
  - Starts working on a big feature while other tasks pile up
  - Big feature gets put on hold
  - Enough time goes by that it's either better to scrap the feature or start over
- When a project gets unfinished, the context of the world changes
  - Has a high likelihood of creating [defects](#defects) as you try to bring the project up to speed
  - Might need to pull [heroics](#heroics) to finish the project
- To avoid, break the project down into the smallest deliverable phases
  - the project is always in some kind of finished and usable state, even if not fully ideal

##### Manual Processes
- Something that is done by a person, even though it is always the same
  - Tends to create [defects](#defects) because people make mistakes
  - Also demands [task switching](#task-switching)
  - Also creates [motion](#motion) because people might need to communicate
  - Makes it difficult to scale the operation
  - Creates [waiting](#waiting)
- Learn how to automate it

##### Extra Processes
- Things you are doing that you probably don't need to do
  - Lead to the same wastes as [manual processes](#manual-processes) but have different solutions
- The solution is to stop doing them
  - Asks the question `Can we not?` to cut extra processes

##### Extra Features
- A feature that isn't adding to the player experience
  - Every feature adds complexity, which leads to [defects](#defects)
- Always be vigilant that the feature pushes the vision of a game that the player cares about
- The best way to deal with them is to cut them

##### Heroics
- When unreasonable acts are required to deliver a required result
  - Crunching
  - When in heroic panic mode, you are creating more of the other kinds of waste
- Heroics are the worst kinds of waste because they are cancerous
- Heroics are performed because processes have broken down

![](https://i.imgur.com/lSZr8Q8.png)

![](https://i.imgur.com/nQNh0X8.png)

![](https://i.imgur.com/zwpkcBb.png)

#### Fixing the problem

##### Making the work visible
- Find all the places they were creating waste
- Twice-Weekly Production Meetings
  - Agree what is going to happen within the next 16 hours of work
  - Shorter sprints led to shorter meetings, which led them to be more responsive and iterative
- Transitioned to using Trello
  - Allow the boards to guide the flow of work to something they can easily see
  - 5 boards:
    - Inbox
    - To-Do
    - Doing (Sprint)
    - Testing
    - Done
###### Rules
1. New tasks go to the inbox and are evaluated next meeting -- avoids being derailed by unplanned work
   - New tasks always go to the inbox first and cannot be put into any other list
   - Each production meeting evaluates the inbox and decides the priority
   - This meant everybody knew what the next two days of work looked like
   - New tasks do not interfere other's work because they are not yet evaluated
2. Time is a constraint, not a flexible resource. Avoids burnout and crunch.
   - Only 16 hours of work can be handed to any one person during that sprint
   - Exceeding demands that person to crunch
   - Refusing to crunch is the core way to bake quality into the production pipeline
3. Work should go through the whole flow. "Testing" step requires that everything be verified before going downstream, reducing [defects](#defects).
   - Keeps work from flowing backwards because errors get fixed at the source

###### Revised Art Asset Pipeline

![](https://i.imgur.com/BPUocYB.png)

- The errors are no longer the programmer's problem

###### The programmer is the bottleneck
Bottleneck
- Part of a process that is receiving more work than it can handle
- Every production process has at least one bottleneck

![](https://i.imgur.com/cHKBFoo.png)

Assets now get longer to create due to the new pipeline which led to reduction of assets output due to testing

![](https://i.imgur.com/ExWnZJN.png)

Simply moving a task to another person doubled the amount of art that can be used in the game

![](https://i.imgur.com/lQdS6Yk.png)

###### Deployments are also bottlenecked
Deployments
- Getting the game into people's hands
- Have been a problem since day 1 because it's difficult
- If a process is painful, you should do it more, not less
- If you don't confront it, you don't learn about it, you don't fix it

Goal: Continuous Deployments
- A constant stream of tiny changes
- Each tiny change gets delivered to QA
- Allows to detect and fix problems immediately
- Fewer catastrophic failures
- Easier to identify where problems emerge
- Quickly fix issues with deployments


![](https://i.imgur.com/OvzPk6g.png)

Due to the time it takes to make a single build, other platforms were untested

GamePipe
- What is the simplest version of the gamepipe that can be used immediately
  1. Builds get uploaded to dropbox when commits are pushed to master
     - Game programmer's time is no longer going into compiling builds
     - No [manual work](#manual-processes) of delivering builds to testers, saving time and reducing [task switching](#task-switching) and [defects](#defects)
     - Environment Configuration is no longer a problem
       - Builds always use the same versions/sdks/etc
       - Weekly builds become daily builds
       - Changes are tested within 24 hours
     - Patch notes were still being written manually
  2. Git commits are converted into patch notes which gets posted into the website
     - Allows for continuous deployments
     - Removes [defects](#defects), like missing changes in the patch notes
     - Git commits become cleaner, more readable, and more useful
  3. Builds now get deployed to Steam
     - Testers always have the latest version of the game automatically
  4. Builds now get deployed to all platforms
  5. Automatic Localization was added
     - New translations get added every version
- A fully manual, 1-hour process becomes 5 seconds to trigger
- Went from weekly testing to continuous testing
- Builds become more stable
- Deployments are painless and easy
- Create a simple automatic deployment pipeline and begin using it as soon as possible. Then, improve it over time.

![](https://i.imgur.com/21dpfJC.png)

###### Business Administration Bottleneck
Employee Training Process
- Trello Board
  - Inbox -> To-Do -> Doing (Sprint) -> Testing -> Done
- Populated the "To-Do" list with training tasks
  - Generate knowledge and insight to how the studio works, and the role of the employee being hired
- Twice-weekly production meetings to review and plan
  - Tasks were broken down on hours
- The new hire always knew what to work on and why
- Later used the same process to hire a full-time QA
- Onboarding was simple and stress free
- Result: Reduced strain on production, increased studio output.

![](https://i.imgur.com/3hEewFa.png)

## Amplifying Feedback Loops

Work flows forwards. Feedback flows backwards!

- Feedback allows us to catch problems, improve processes, and build quality into the pipeline.
- Develop tools and systems to gather feedback from people downstream.

### The QA Testing Pipeline

![](https://i.imgur.com/21dpfJC.png)

- Speeding up the QA pipeline would lead to more work because reports issues are fully manual
- Used Trello API so that issues get converted to cards
- Turned patch notes into a QA testing checklist
  - On the developer side, there is a count of the number of testers that have reported that test
  - Let's them know the test coverage

![](https://i.imgur.com/xH0Ugkb.png)

![](https://i.imgur.com/YtB4boV.png)

## Continuous Learning

Keep iterating on your processes!
- Ensure everyone on the team has the right to experiment
  - People offer risky ideas, and management needs to hear those out
- Reinforce Culture of psychological safety
- Your work culture is a result of the structures and processes you use

What structure to reinforce learning?
- New structure: Formalized Quarterly Reviews
  - Every quarter team members get questionnaires
    - Identifies how they're feeling about their work in ways they believe their time/talent are wasted
    - use these answers plus waste analysis to look for ways to improve our processes

Routine Evaluation Structures Matter
- use them to create a culture of learning

# Recap
1. Master the flow of work
   1. Make sure the work flows forwards
   2. Watch out for bottlenecks
   3. Cut down on defects
   4. Eliminate Waste
2. Amplify feedback loops
   1. Make sure you are getting the information you need from the people downstream to make their and your lives better
3. Iterate & Learn
   1. Create a culture of continuous learning and experimentation
   2. Constantly improve and deliver value to your players

# The Curve Ball
- Mario Maker 2 is announced and it is launching the same month as Levelhead
- Beating Mario Maker 2 to launch meant that the only available date was on April - two months earlier than planned
- The target platform was changed to steam
- Pre-Alpha testing began on March 1 with a small group
- Alpha testing began on March 8 to a larger group
- The game was launched in early access on April 18
- Instead of delivering the game to players in 3 months, they had 2 weeks

## Because of the DevOps pipeline
- Builds were already stable and easily patchable
  - Priorities were shifted to get features to alpha
- In two weeks, alpha starts, and
  - No major problems
  - Thousands of hours testing: one crash. Fixed, tested, deployed within hours
- Early Access Launch Day
  - Everything was fine
  - No emergency patches

# 11 Months Later
- Still doing continuous deployments
- 97% positive on Steam
- 2-3 content patches delivered to players per month
- Patches are no big deal
- No heroics, even with 6 platforms and 11 languages with a team of 6

The stresses of game development are from bad practices

# The Three Ways
1. Managing the Flow of Work
2. Amplifying Feedback Loops
3. Continuous Learning

# Big Takeaways
1. Make the work visible
2. Waste is worse than you think
3. Focus efforts on bottlenecks
4. Focus on small batch delivery
5. Use continuous deployments to improve quality

# The types of Waste
1. Motion
2. Task Switching
3. Defects
4. Waiting
5. Manual Processes
6. Extra Processes
7. Extra Features
8. Unfinished Projects
9. Heroics