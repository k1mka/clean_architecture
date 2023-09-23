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

4. **CONFIG folder** 
   The config folder can contain both application configurations, for example Environment Variables, and Environment Services in order
   to launch applications with the corresponding flags.

5. **DATA folder**
   Data is the bottom level, responsible for directly working with raw data from different data sources (REST API, GraphQl, Sqlite, etc.).
   The raw data will then be collated or transformed into models. Models at the data level are different from models at the Entities level, if we 
   want to change the raw data, these changes will not affect the internal entities (Domain’s Entities). The date also contains local storage, both 
   its abstraction and implementation. In the folder with local data, you can create a facade folder, which will contain local storage solutions, 
   this can be a regular Shered Preff or some kind of Secure Storage for storing tokens. In the folder with the remote storage, you can create an API 
   folder to divide the application flow in as much detail as possible, for example, requests for authorization separately, requests for filling out 
   a profile separately. It all depends on the scale of your application. And of course, our Network Service, in the data folder there is a well- 
   established solution with the help of which we will send requests to the server.

6. **Domain folder**
   The domain layer contains only internal objects, which means that our domain objects are completely independent of any changes that may occur 
   outside of this layer.The presentation and data layers depend on this layer because the data layer will implement everything that has ever been 
   written in the domain, and the presentation layer will use these implementations to be used as injected dependencies.
   This layer contains a mapper that transfers data from data-level models to the domain-level model and vice versa, in order to flexibly replace 
   databases in the future.

7. **Presentation folder** (UI)
