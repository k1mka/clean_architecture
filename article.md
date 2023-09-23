# clean_architecture

**Understanding a project's architecture is a fundamental aspect of software development.**

Clean architecture is a way of designing software that makes code more understandable and flexible. It breaks the application into independent parts, each of which performs its own specific task, and at the same time they are weakly dependent on each other. This makes it easier to change and expand the application without affecting other parts of the application. The point is to make the code cleaner and more organized, making it easier to maintain and develop.

![Architecture diagram, if not displayed, look in the repository files!](https://github.com/k1mka/clean_architecture/blob/main/sheme.jpg)

1. **LIB root folder**
   Contains the top-level main function, which is responsible for launching the entire program, including initializing various dependencies when the 
   application starts. Main can reference appEntry class, this file is part of the Flutter application and is responsible for setting up and 
   configuring the application, including setting up the theme, localization, routing, and dependency injection. You can do all this in main, but 
   it’s better to separate it. This will make the code more modular.

2. **SRC folder** 
   The scr folder contains three layers of the application, presentation (ui), domain (bl), data and also the config and core folders.

3. **CORE folder** 
   The core folder the main folder is much more important, it includes the core things that we need throughout the entire application (globally), for 
   example DI or application theme, so if we have a task/action that everyone will need, then it’s better to put it in the core. It also includes 
   some other folders such as (Resources, Utilities, etc.).
