---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
# What's up?

Some time ago I realized that my C++ skills have somehow rotten and decided that I will do something about it. And here we go. I decided that I will implement something simple but while doing it, I will use modern tools and methodologies (techniques, if you will) for C++.

I decided that the "thing" which I shall implement will be a collection of generic containers which store their elements on the stack. I will try to keep it as independent from std as possible (so that it can be used in bare-metal projects). I will thrive for keeping everything constexpr and noexcept - which I trully like. Perhaps I will make the containers compliant with std algorithms but that is an option.

The containers I would like to implement are:

1. Array - collection of N items - you cannot add or remove them - you can only change their values.
2. Stack - collection of 0 to N items - you can add or remove them but the fastest operations are on the top of the stack.
3. Wheel - circular buffer - collection of 0 to N items - adding N+1'th element takes place of the 1'st element and so on.
4. Queue - collection of 0 to N items - it's easy to add elements at the end and easy to remove elements at the front.
5. Set - collection of ordered 0 to N items without duplications.
6. Chain - double linked list - collection of 0 to N items - it's easy to insert or remove at any place but in order to find specific element it needs to be traversed.
7. [optional] Map - collection of 0 to N key-value pairs.

Huh! That's a lot of code to be written! Perhaps the task is simple but that does not mean it will be easy. There are couple of tools I would like to exploit during the process:

1. CMake - I am a big fan of CMake but I haven't used it in a while so it's time to update my knowledge.
2. Conan - I was super excitet about cargo package manager for Rust lang - let's see what does C++ community have to offer.
3. GoogleTest + GoogleMock - it's about time to invest some points in auto testing skills!
4. clang-format - yeah - I like the code to be pretty.
5. Git - but of course! I am currently condemned to SVN and I would love to see the add/commit/push trio again!

Above all of that I will try to do my best in keeping up with TDD (Test Driven Development). Although in case of simple tasks, the fingers are just screaming to go straight for the implementation, I will patiently try to think about examples (and interfaces) first.

I write code in Visual Studio Code on Ubuntu. I'm a big fan of VS Code but Ubuntu is starting to annoy me (e.g. with dummy notifications that my file browser has been successfully opened - surprise!) so it might change to Arch during the process. I compile with g++ 9.3 and use cmake 3.16.

# Let's go!

Let's start with some basic organization of a project. We will call it "Stack Containers" - seems to be clear and simple.

mkdir stack-containers
cd stack-containers

For sure we will have some source files and some tests. I think the implementation will be header only (since the containers are goint to be templates) so there is no need for a separate include folder (which I would normally add).

mkdir source
mkdir test

Since we are using CMake, let's add a configuration file.

touch CMakeLists.txt
