## Continuous Integration Basics ##

### Practices of Continuous Integration ###

Key practices that make up effective CI.

#### **Maintain a Single Source Repository** ####

Software projects involve lots of files that need to be orchestrated together to build a product. Keeping track of all of these is a major effort, particularly when there's multiple people involved. So it's not surprising that over the years software development teams have built tools to manage all this. These tools -called Source Code Management tools, configuration management, version control systems and repositories, or various other names - are an integral part of most development projects. The sad and surprising thing is that they aren't part of *all* projects. It is rare, but I do run into projects that don't use such a system and use some messy combination of local and shared drives.

So as a simple basis make sure you get a decent source code management system. Cost isn't an issue as good quality open-source tools are available. The current open source repository of choice is Subversion. (The older open-source tool CVS is still widely used, and is much better than nothing, but Subversion is the modern choice.) Interestingly as I talk to developers I know most commercial source code management tools are liked less than Subversion. The only tool I've consistently heard people say is worth paying for is Perforce.

Once you get a source management system, make sure it is the well known place for everyone to go get source code. Nobody should ever ask "where is the foo-whiffle file?" Everything should be in the repository.

Although many teams use repositories a common mistake I see is that they don't put everything in the repository. Everything you need to do a build should be in there including: test scripts, properties files, database schema, install scripts, and third party libraries. I've known projects that check their compilers into the repository. **The basic rule of thumb is that you should be able to walk up to the project with a virgin machine, do a checkout, and be able to fully build the system.** Only a minimal amount of things should be on the virgin machine - usually things that are large, complicated to install, and stable. An operating system, Java development environment, or a base database system are typical examples.

You must put everything required for a build in the source control system, however you may also put other stuff that people generally work with in there too. Integrated Development Environments(IDE) configurations are good to put in there because that way it's easy for people to share the same IDE setups.

One of the features of version control systems is that they allow you to create multiple branches, to handle different streams of development. This is a useful, nay essential, feature - but it's frequently overused and gets people into trouble. Keep your use of branches to a minimum. In particular have a **mainline:** a single branch of the project currently under development. Pretty much everyone should work off this mainline most of the time. (Reasonable branches are bug fixes of prior production releases and temporary experiments.)

In general you should store in source control everything you need to build anything, but nothing that you actually build. Some people do keep the build products in source control, but I consider that to be a smell - an indication of a deeper problem, usually an inability to reliably recreate builds.

#### **Automate the Build** ####

Getting the sources turned into a
