[[ReadItLater]] [[Article]]

# [Building my second brain 🧠 with Obsidian](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/)

This article will take [Obsidian](https://obsidian.md/) as an example to share my practice of using Obsidian to build a second brain!

This article is also available in [简体中文](https://quanru.github.io/2023/06/18/%E4%B8%80%E7%A7%8D%E5%AE%9E%E7%94%A8%E6%96%B0%E5%9E%8B%20Obsidian%20%E5%AE%9E%E8%B7%B5%E4%B9%8B%E6%9E%84%E5%BB%BA%E6%88%91%E7%9A%84%E7%AC%AC%E4%BA%8C%E5%A4%A7%E8%84%91%20%F0%9F%A7%A0/).

## [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Foreword "Foreword")Foreword

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#What-is-Obsidian "What is Obsidian?")What is Obsidian?

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B-%E6%A0%87%E6%B3%A8-EN.png)

This is how it introduces itself on the official website:

-   [Obsidian](https://obsidian.md/) is the private and flexible note‑taking app that adapts to the way you think.

I mainly fancy its rich plugin ecology. If you like Vscode , then you will probably like Obsidian too, but Vscode is used to write code, while Obsidian is used to take notes.

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#First-Brain-vs-Second-Brain "First Brain vs Second Brain")First Brain vs Second Brain

The first brain is our real brain. As long as we are alive, this brain is constantly running, performing tasks such as knowledge management , task management, goal management, etc. Most of the time we can’t use our first brain with multitasking, so The first brain is more like a CPU, and various tasks are sharding the CPU. When there are many tasks to be dealt with, the brain will be overwhelmed, because the brain has to deal with the current task and maintain the context of other tasks to switch tasks, making us unable to focus on the execution of the current task. An external system is needed to assist the first brain, which is the second brain.

The second brain is an external system. If the first brain is compared to a CPU, the second brain is more like a storage system. It is like a cache between the first brain and the real world, reducing the burden of the first brain. It can be compared to memory and hard disk, but memory communicates more frequently with the CPU (first brain) and reads faster than hard disk. This storage system stores things that the current first brain does not need to pay attention to at all times. Of course, these things have to be decided by the first brain to decide whether it is necessary to store them. The content can be records, to-do, processes, and the carrier can be text, pictures, and videos..

For example, when we use the second brain for task management, important and urgent matters are stored in memory, and non-important and non-urgent matters are stored on the hard disk; this week’s tasks are stored in memory, and this month’s tasks may be stored on the hard disk. So by using the second brain, we can focus on the present moment without stress and switch contexts when necessary.

This article will use Obsidian as an example to share my practice of building a second brain! You call it a second brain, but looking at this brain from a different perspective, I can also call it “LifeOS”, because I record it from life and work; I can also call it “Programmable Personal Productivity System “, I wrote a lot of code on it to do some queries and automation, and it is also a productivity system I use to manage tasks and goals; it is even a bit like “ Monorepo Engineering”, each folder is a project, and the README.md in the project describes the current project like package.json Meta Information .

📢 Note: This system is not the kind of “Have a process first, and then go according to the system to implement the system from top-down”, is my use of Obsidian process gradually formed, but also has been iterative, let’s set the current version as 1.0, now share it is to give you a little inspiration, to improve their own system! ~In addition, you may need to have a programming foundation, because I wrote a lot of custom~ ~JavaScript~ ~scripts (does not rule out the possibility of plugins), but if you follow my system completely, it does not need to understand the code, download and use it!~ An [Obsidian Periodic PARA](https://github.com/quanru/obsidian-periodic-para) plugin has been written to support this system!

## [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#My-practice "My practice")My practice

I use two systems, one is the knowledge management system, and the other is the periodic note system. The former takes the project/area/resource as the dimension for knowledge management, and the latter takes the time as the dimension for task/goal/time management.

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Two-systems "Two systems")Two systems

![](_Inbox/Read%20Later/assets/%E7%AC%AC%E4%BA%8C%E5%A4%A7%E8%84%91%E7%B3%BB%E7%BB%9F%E5%9B%BE-EN.png)

-   Knowledge management : implementation of the [PARA](https://fortelabs.com/blog/para/) system
    -   Projects - > A project is a series of tasks related to a goal, with a deadline
    -   Areas - > A field is a field of activity that requires certain standards to be maintained for a certain period of time
    -   Resources - > Resources are topics or topics of ongoing interest
    -   Archives - > Archives are inactive entries from the three categories above
-   Periodic note
    -   Long-term type: top-down, focus on long-term goals
        -   Three-year goals
        -   Yearly goals
        -   Quarter goals
    -   Short-term type: Bottom-up, focusing on short-term tasks
        -   Monthly tasks
        -   Weekly tasks
    -   DailyLog: Capture ideas and insights to achieve self-awareness; time-consuming statistics to ensure focus on projects

In the PARA system, the closer to Project, the higher its operability; In the periodic note system, the longer the note’s time scope, the lower its predictability;

These two systems are equivalent to creating two contexts that keep me focused

-   One is time-based (periodic notes), that is, when I reach a certain time node, I will take notes on the job based on the corresponding period, and there is enough context in the notes;
    
-   The other is topic-based ( PARA ), that is, when I want to investigate a topic, I focus on Index(README.md) based on the corresponding topic, and I have collected a lot of context in my notes;
    

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#AOP-subsystem "AOP subsystem")AOP subsystem

Under the above two systems, there is a hidden task/goal/time management subsystem, which I mainly manage through “periodic notes”:

-   Task management
    
    -   Collect through DailyLog/weekly notes
        
    -   Organize by weekly/monthly notes
        
-   Goal management
    
    -   Planning annual goals through yearly notes
        
    -   Split annual goals through quarterly notes
        
    -   Planning to-do items through monthly notes.
        
        -   Top-down tidying (through goals splitting)
            
        -   Organize from bottom to top (splitting by collection- > DailyLog/weekly notes)
            
-   Time management
    
    -   Manually count the time consumption and proportion of each project through a DailyLog, give feedback and adjust the time cost.
        
    -   Use scripts to automatically count the time consumption and proportion of each project through DailyLog, weekly record, monthly record, quarterly record, and annual record for review time overhead
        

You may be curious that the above subsystems seem to only use “periodic notes”. In fact, the various subsystems are connected in two ways between the two parent systems.

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Connection "Connection")Connection

> How the systems relate

#### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Tag-connection "Tag connection")Tag connection

![](_Inbox/Read%20Later/assets/%E7%AC%AC%E4%BA%8C%E5%A4%A7%E8%84%91%E7%B3%BB%E7%BB%9F%E5%9B%BE-%E8%BF%9E%E6%8E%A5-EN.png)

Use the first-level folder under PARA as a special tags (not necessarily exactly the same as the folder name) in the “periodic Note”, so that each first-level folder can be uniformly indexed in the same way. This ensures that the README.md index under each PARA folder has all the context of the current topic:

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B-%E6%A0%87%E6%B3%A8-EN.png)

#### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Project-connection "Project connection")Project connection

Projects are generated by initiating items in Knowledge Management . In order to increase attention to the project, a list of “First Things” or a “Project List” is set in each type of periodic note, such as

-   The “Project List” in the DailyLog, which is a snapshot of the current Project List, used to count the time spent on each project and its proportion that day, to ensure that enough time is spent on the project
    
-   The “First Things Dimension” in the weekly and monthly notes is a list obtained by automatically merging deduplicate from the diaries of this week and this month, which is used to arrange the tasks of the project dimension and subsequent review
    
-   The “First Things Dimension” of quarterly note, which is a snapshot of the current area list, used to arrange the goals of the important dimension and subsequent review
    
-   The “First Things Dimension” in the yearly note is a list obtained by automatically merging deduplicate from the quarterly record of the year, which is used to set the goal of the area dimension and subsequent review
    

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B-EN.png)

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Retrieval "Retrieval")Retrieval

-   Tag
    
    -   For example, DailyLog [holidays](https://github.com/quanru/obsidian-example-LifeOS/blob/main/PeriodicNotes/2023/Daily/06/2023-06-01.md#L3) , [vacation](https://github.com/quanru/obsidian-example-LifeOS/blob/main/PeriodicNotes/2023/Daily/06/2023-06-11.md#L4) tags s
-   File index
    
    -   For example, each project’s [README.md](https://github.com/quanru/obsidian-example-LifeOS/blob/main/1.%20Projects/%E5%88%86%E4%BA%AB-2023%20WOT%20%E5%88%86%E4%BA%AB%E4%BC%9A/README.md) indexes the project’s tasks, daily record, and context
-   Folder
    
    -   For example, each PARA directory uses a consistent directory structure

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Review "Review")Review

-   The review is mainly aimed at the projects in this periodic, and the tasks for the next periodic are planned while reviewing
    
-   Weekly review current week’s DailyLog, monthly review weekly review, quarterly review monthly review
    

## [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Demo-description "Demo description")Demo description

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#%E2%80%9CDailyLog%E2%80%9D-and-%E2%80%9CProject-README%E2%80%9D "“DailyLog” and “Project README”")“DailyLog” and “Project README”

-   Used for daily management, including Project List, daily record, clock in habit, energy allocation, done task today and other modules
    
-   The “Project List” in the DailyLog is a snapshot of the current project (i.e. in the Projects folder)
    

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B-EN.png)

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#%E2%80%9CWeekly-Note%E2%80%9D-and-%E2%80%9CMonthly-Note%E2%80%9D "“Weekly Note” and “Monthly Note”")“Weekly Note” and “Monthly Note”

-   Used to schedule weekly and monthly tasks, including task and review modules
    
-   In the weekly and monthly note, the “First Things Dimension” is a collection of snapshots of the “Project List” of the DailyLog for this period (automatically generated).
    
-   In the weekly and monthly note, the “ review “ is mainly carried out for the projects in the current periodic
    

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B2-EN.png)

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#%E2%80%9CQuarterly-Note%E2%80%9D-and-%E2%80%9CYearly-Note%E2%80%9D "“Quarterly Note” and “Yearly Note”")“Quarterly Note” and “Yearly Note”

-   Used to set quarterly and yearly goals, including goals and review modules
    
-   In the quarterly note, the “First Things Dimension” is a snapshot of the current area (that is, under the Areas directory)
    
-   In the yearly note, the “First Things Dimension” is a collection of snapshots of the “First Things Dimension” of the quarterly note of the current period(automatically generated).
    
-   In the quarterly and yearly note, the “ Review “ is mainly carried out in the areas in this period
    

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B3-EN.png)

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#%E2%80%9C-PARA-Index%E2%80%9D-and-%E2%80%9CTask-Index%E2%80%9D "“ PARA Index” and “Task Index”")“ PARA Index” and “Task Index”

![](_Inbox/Read%20Later/assets/LifeOS-%E7%A4%BA%E4%BE%8B4-EN.png)

## [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#How-to-start "How to start?")How to start?

1.  Download [Example](https://github.com/quanru/obsidian-example-LifeOS/releases/latest/download/LifeOS.zip)
2.  Use obsidian open the vault

## [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Tips-for-practice "Tips for practice")Tips for practice

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Cache-mechanism "Cache mechanism")Cache mechanism

Keep most of the attention in the “project” by creating tasks and quickly placing them in the cache zone

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Task-list "Task list")Task list

Do not have too much pressure on the task record, writing down does not mean that you must do it; writing down can reduce the burden on your mindset, do not always think about this task, and are not afraid to forget this task; I have a lot of tasks to write down, the follow-up evaluation has not been achieved.

We just need to ensure that certain mechanisms can recall these recorded tasks, such as

-   Use the tasks plugin to do some task list [query view](https://github.com/quanru/obsidian-example-LifeOS/blob/main/TASK.md)
    
-   Each periodic note contains a [task list](https://github.com/quanru/obsidian-example-LifeOS/blob/main/PeriodicNotes/2023/Weekly/2023-W22.md#%E6%9C%AC%E5%91%A8%E6%94%B6%E9%9B%86)
    
-   [Task list](https://github.com/quanru/obsidian-example-LifeOS/blob/main/1.%20Projects/%E5%88%86%E4%BA%AB-2023%20WOT%20%E5%88%86%E4%BA%AB%E4%BC%9A/README.md#%E4%BB%BB%E5%8A%A1) in project index file
    

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Task-reminder "Task reminder")Task reminder

I think there are three types of task reminders

-   Strong reminders, such as grab concert tickets, which need to start on time, so you need a strong reminder, set an alarm clock through your phone to remind you
-   Weak reminders, which need to be completed on a certain day, such as credit card repayment, loan repayment, etc., can be set reminder through GTD software
-   List type, used to record tasks, allowing you to coordinate and arrange them in the future, and can be converted into strong reminder or weak reminder events as needed, somewhat similar to the inbox in GTD

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Micro-habits "Micro habits")Micro habits

![](_Inbox/Read%20Later/assets/%E7%A6%8F%E6%A0%BC%E8%A1%8C%E4%B8%BA%E6%A8%A1%E5%9E%8B-EN.png)

-   I will list some micro-habits in the DailyLog note, remember that it is not a task, you can finish it or not, mainly used to remind you of “these micro-habits, do you consider doing it today?”, that is, when I have “ability” and “motivation”, it plays the role of “prompt”, such as:
    
    -   Micro habits
        -   Get up and drink water as soon as you hear the alarm clock go off
        -   Put on headphones as soon as you get off the car to listen to the podcast
        -   Open Kindle as soon as you get on the subway
        -   As soon as you arrive at your workstation, write down three things to do
        -   Start doing business as soon as 10:30

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Easy-to-refactor "Easy to refactor")Easy to refactor

In each periodic note, modules with the same function use the same statement. For example, “Tasks collected in this periodic” are inserted by inserting the following query statement, and the variables of “this periodic” are provided by parsing the current file name, which makes it very convenient to reconstruct all periodic files in batches. You only need to replace them in batches:

|   1   2   3      |   \`\`\`PeriodicPARA   TaskRecordListByTime   \`\`\`      |
| --- | --- |

### [](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/#Make-good-use-of-shortcuts "Make good use of shortcuts")Make good use of shortcuts

Set globally consistent shortcuts, so that no matter which software can use the same shortcut to evoke the same function, here are some of my settings:

-   Cursor movement
    -   Rule: Control + direction first letter/ VIM direction
    -   Example:
        -   A: Head of line
        -   E: End of line
        -   F/L: Forward
        -   B/H: Backward
        -   N/J: Next line
        -   P/K: Previous line
        -   W: Delete a word(Backward)
        -   D: Delete a character(Forward)
-   Window management
    -   Rule: Command + Option + First Letter
    -   Example:
        -   L: Left half screen
        -   R: Right half screen
        -   C: centered
        -   M: Maximize
        -   `[` : Show/hide left sidebar
        -   `]` : Show hidden right sidebar
        -   ‘: Show/Hide bottom bar
        -   T: Create a new Tab (under more specific windows, use Command + T for the top-level Tab)
        -   W: Close Tab (more specific window, top-level Tab uses Command + W)
        -   J: Next Tab
        -   K: Previous Tab
-   Doc editor
    -   Rule 1: Command + Option + Number/Symbol
    -   Example:
        -   1: Markdown first-level title
        -   2: Markdown secondary title
        -   3: Markdown Level 3 Headers
        -   4: Markdown Level 4 Headlines
        -   5: Markdown Level 5 Headlines
        -   6: Markdown Level 6 Headlines
        -   Bulleted List:~
        -   Strikethrough: -
-   Functional class
    -   Rule: Control + first letter
    -   Example:
        -   C: Copy link(Obsidian block link, Arc browser link, VScode git link)
        -   D: Download
        -   I: Add to inbox
        -   K: Quick Search