---
title: "Debugging code for absolute beginners"
description: "If you are debugging for the first time, learn a few principles to help you debug applications with Visual Studio"
ms.custom: ""
ms.date: "06/18/2018"
ms.technology: "vs-ide-debug"
ms.topic: "conceptual"
helpviewer_keywords:
  - "debugger"
author: "mikejo5000"
ms.author: "mikejo"
manager: douge
ms.workload:
  - "multiple"
---
# How to debug for absolute beginners

Learn the very basics of how to debug using a debugger. If you are getting ready to try out a debugging tool like Visual Studio and this is the first time that you've tried to debug an application, then you're in the right place. When you use a debugger for the first time, it's normal to hope (and expect) that whatever debugging tool you're using will magically show you all the bugs in your code. Unfortunately, it's not that easy. Debugging is a learned skill, and it takes time and practice to learn how to debug effectively. So before we teach you how to debug, we give you some general tips and principles.

First, it might be helpful to answer some basic questions such as "What is debugging?" and "What is debugging mode?"

* *Debugging* is the process of removing bugs from your code.

* *Debugging mode* means running your app (executing code) while a debugger is attached to your application. With a debugger attached, you can see what your code is doing while it runs. For example, you can inspect your app state (look at variables), see what functions are getting called, and try to find bugs. In the Visual Studio documentation, when we want you to enter debugging mode, we usually just say "Start the debugger" or "Run your app in the debugger".

## Clarify the problem by asking yourself the right questions

It helps to clarify the problem that you ran into before you try to fix it. We expect that you already ran into a problem in your code, otherwise you wouldn't be here trying to figure out how to debug it! So, before you start debugging, ask yourself a few questions.

* What did you expect your code to do?

* What happened instead?

    If you ran into an error (exception) while running your app, that can be a good thing! An exception is an unexpected event encountered when running code, typically an error of some kind. The [Exception Helper](../debugger/debugger-feature-tour.md#exception) in Visual Studio puts your app into debugging mode, takes you to the exact place in your code where the exception occurred, and gives you an error message to help you investigate possible fixes. (But before you investigate, finish reading this article.)

    If something else happened, what is the symptom of the problem? Do you already suspect where this problem occurred in your code? For example, if your code displays some text, but the text is incorrect, you know that either your data is bad or the code that set the display text has some kind of bug. To fix a problem like this, you most likely need to start your application with the Visual Studio debugger attached and look at your variables. (But first, continue reading this article.)

## Examine your assumptions

Before you investigate a bug or an error, think of the assumptions that made you expect a certain result. This may be a long list, so here are a few examples of assumptions that are easy to make but not necessarily true.

* You are using the right API (that is, the right object, function, method, or property). An API that you're using might not do what you think it does. (After you examine the API call in the debugger, fixing it may require a trip to the documentation to help identify the correct API.)

* You are using an API correctly. Maybe you used the right API, but didn't use it in the right way.

* Your code doesn't have any typos.

* You made a change to your code and assumed it is unrelated to the problem that you're seeing.

* You experienced a change in your environment (such as a tool or library update) and assumed it is unrelated to the problem that you're seeing.

* You expected an object or variable to store a certain value (or a certain type of value), but it doesn't.

* You understand this code well enough to debug it. It is often more difficult to debug someone else's code. If it's not your code, it's possible you might need to spend time learning what the code does before you can debug it effectively.

    > [!TIP]
    > Start small, and start with code that works! Sometimes, it is easier to fix a large or complicated set of code by starting with a small piece of code that demonstrates the core task you are trying to achieve (that is, copy a working sample). Then, you can modify or add code incrementally, testing at each point for errors.

By knowing your assumptions, you may reduce the time it takes to find a problem in your code. You may also reduce the time it takes to fix a problem.

## Step through your code in debugging mode to find where the problem occurred

If you didn't get an exception, use the debugger to find the exact place where the problem (or symptom of the bug) occurred. Before you start, do your best to try to find the specific region of code where the problem is occurring, then set a [breakpoint](../debugger/using-breakpoints.md) where that code begins. Breakpoints are the most basic and essential feature of reliable debugging. A breakpoint indicates where Visual Studio should suspend your running code so you can take a look at the values of variables, or the behavior of memory, or whether or not a branch of code is getting run. You can set a breakpoint by clicking in the left margin next to a line of code.

![Set a breakpoint](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

Once you've set a breakpoint, start the debugger (press **F5** or the **Start Debugging** button ![Start Debugging](../debugger/media/dbg-tour-start-debugging.png "Start Debugging") in the Debug Toolbar), and the app will pause when the code where you set the breakpoint executes (if it doesn't pause, the code didn't execute). Then use [step commands](../debugger/navigating-through-code-with-the-debugger.md) such as **F10** and **F11** to advance the debugger and run your code. While debugging, your app code executes like normal. While running your app in the debugger, look for the problem that you identified.

> [!NOTE]
> If it is difficult to identify the region of code where the problem occurs, set a breakpoint in code that runs before the problem occurs, and then use step commands until you see the problem manifest. You can also use [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) to log messages to the **Output** window. By looking at logged messages (and noticing which messages were not yet logged!), you can often isolate the region of code with the problem. You may have to repeat this process several times to narrow it down. If the problem is occurring somewhere within a loop that repeats many times (and is therefore hard to reproduce), a [conditional breakpoint](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) can help.

## When you find the region of code with the problem, use the debugger to investigate

To find the cause of a problem, inspect the problem code while running your app in the debugger:

* [Inspect variables](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) and check whether they contain the type of values that they should contain. If you find a bad value, find out where the bad value was set (to find where the value was set, you might need to either restart the debugger, look at the [call stack](../debugger/how-to-use-the-call-stack-window.md), or both).

* Check whether your application is executing the code that you expect. (For example, maybe the code that you're using handles (hides) an exception, and you didn't realize that an exception occurred until you see the exception handler code get invoked.)

## Next steps

In this article, you've learned a few general debugging concepts. Next, you can start learning how to debug with Visual Studio.

> [!div class="nextstepaction"]
> [Debugger feature tour](../debugger/debugger-feature-tour.md)
