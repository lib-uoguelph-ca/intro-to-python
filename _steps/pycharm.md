---
nav_previous: setup
nav_next: functions
layout: page
---

Now that we've got our project set up in PyCharm, it's time to familiarize ourselves with the PyCharm interface. 

The PyCharm interface is divided into a number of panels. Let's start by digging a little deeper into a few of them. 

## The Project Explorer

![The project explorer](../assets/images/pycharm-project-pane-empty.png)

The left most pane in is the project explorer, the main way that we'll organize and explore the files that make up our project. Right now, our project doesn't include any files, so there's not much to see. Let's fix that by adding a few files:

In the project explorer, right click on the folder, *pycharm-introduction* and select *New* > *Python File*. 

![The context menu for creating a new file](../assets/images/pycharm-new-file.png)

PyCharm will then ask us to give our file a name. Let's call it "analysis.py". As we work through our lessons today, this file will be the script we'll do our data analysis in.

Let's create one other file before we move on, a scratch file. A scratch file isn't really intended to be a part of our final project. Instead they're temporary files where we can write and test our python code without risk of ruining the work we've done so far.

Again, right click on the folder, *pycharm-introduction* but this time choose *New* > *New Scratch File*. PyCharm will then ask us what kind of scratch file we'd like to create. As you can see, while PyCharm is a Python IDE, it's able to work with a very wide variety of file types and languages. Find *Python* in this list and select it. Note that you can type to narrow down the list of options.

Now that we've got a couple of files added to our project, the project explorer has updated accordingly:

![The project explorer with some files](../assets/images/pycharm-project-pane.png)

You can think of the Project Explorer pane as your file explorer on Windows, or as a Finder window on the mac. We can do all the same things including creating directories, renaming, and moving files. 

<div class="aside" markdown="1">

### How Should I Organize My Files?

While you can do all of your work in a single python file, for larger projects this can get unwieldy and difficult to navigate. For that reason, it's often a great strategy to break your code up into different files. When you do this, it's common convention to group your code into files that serve a similar purpose. For example you might have all the code dedicated to cleaning data in one file, analysis in another, and visualization in a third.

</div>