# Standarts and Best Practices

So what are standarts and best practices? As you can imagine, it is pretty fucking self-explainatory. While we code or create any kind of software we need standarts so that the work we produce is not bad. You can think of it like food production. If the company does not follow the rules and standarts the food they produce wont even hit the shelves because the government and licesing agencies wont let them. However, that is not the case with software engineering. Even though we like our standarts there is no one to empose them on a small/medium or even large programs.

You might think that we shouldn't be this fanatic about standarts when it comes to software since it is just abstract right? What happens when an aircraft or an electric car crashes just because of badly written code? You see, abstract becomes physical real quick. That is why we should always stick to best practices and standarts that are set out by the community of the people we trust and respect. 

## When to use Best Practices?

Theoritcally you can startusing best practices at any point of the project however it is BEST to add it from the start. Because it becomes harder to maintain if the project is too big and the code becomes more nebulous and complicated. If everyone agrees to a set of terms from the begining there will be very little confusion about the project.

## Why do we need this?

As we have mentioned above, it is extremly important that you follow some kind of guidelines while coding a project because lets face it, you wont be the only one to work on that project in the future. If every person who join the project add their own style to the code it will be unmaintanable in the long run. Just think would 10 different writers be able write a single book? Yes, but the style of the book would shift from chapter to chapter and hinder the progress of the book.

## How are we going to establish best practices?

So there are many and many establihsed best practices on about writing a project but do not try to do everything at once. Start out small and build your own standarts. That "build your own" phrase does not mean that you should create a new unheard practice. No it necessarily means that choose a best practice to follow and build on top of it to your own taste.

But regardless of having a lot of best practices to follow there are basics and it is called the folder structure. Weather you are coding a python, C/C++, JavaScript project nearly all of the projects folder structure startout like this:
```
docs/index
module/core
tests/core
LICENSE
README.md
requirements.txt
setup.sh
```

So lets talk about each file we have written above:
  - `README` -- this is where you describe what your project is and where to find the neccessary information. It is a index like in a book.
  - `LICENSE` -- this license is a legal file that shows who can use and own the code.
  - `module/` -- this folder contains the actual code of the program. So that you have a single point of entry to all of your project code.
  - `requirements.txt` -- Here, you mention the modules and dependencies of the project- the things it will not run without.
  - `setup.sh` -- this is where you write your setup, build .. etc. scripts to automate the repetetive stuff.
  - `docs/` -- this is where you will write your documentation
  - `tests/` -- this is where you will write your tests

### Language Standarts

As luck would have it programming is starting to mature. So you wont have to resort to 3rd party solutions when it comes to defining a standart. For example nearly all of the languages out there have their own best practices and standarts for writing the language. For example `python` has a file named `PEP8` that shows and defines everything out there for python standarts. And you can easily find other standarts by just typing out `X Language Best Practices and Standarts` on google.
  
