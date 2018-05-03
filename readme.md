
<p align="center">
<img src="https://i.imgur.com/rEXcoMn.png" width="160px"> 
</p>

<p align="center">

<img src="https://travis-ci.org/MasoniteFramework/masonite.svg?branch=master">
<img src="https://img.shields.io/badge/python-3.4+-blue.svg" alt="Python Version"> <img src="http://pepy.tech/badge/masonite?1" alt="License">  <img src="https://img.shields.io/github/license/MasoniteFramework/masonite.svg" alt="License"> 
<img src="https://coveralls.io/repos/github/MasoniteFramework/core/badge.svg?branch=master" alt="License"> 


</p>

## About Masonite

Masonite is the rapid application Python development framework that strives for elegant, readable, and beautiful syntax. Masonite makes building web applications fun, enjoyable and scalable. Masonite takes much of the pain out of developing web applications from simple payment systems to removing mundane development tasks with a command line companion tool called craft commands. Masonite removes much of the mundane tasks of building web applications by:

* Having a simple and expressive routing engine
* Extremely powerful command line helpers called `craft` commands
* A simple migration system, removing the "magic" and finger crossing of migrations
* A great Active Record style ORM called Orator
* A great filesystem architecture for navigating and expanding your project
* An extremely powerful Service Container (IOC Container)
* Service Providers which makes Masonite extremely extendable

## Learning Masonite

Masonite strives to have extremely comprehensive documentation. All documentation can be [Found Here](https://masoniteframework.gitbooks.io/docs/content/) and would be wise to go through the tutorials there. If you find any discrepencies or anything that doesn't make sense, be sure to comment directly on the documentation to start a discussion!

## Linux

If you are running on a Linux flavor, you’ll need a few extra packages before you start. You can download these packages by running:

```
$ sudo apt-get install python-dev libssl-dev
```

Instead of `python-dev` you may need to specify your Python version

```
$ sudo apt-get install python3.6-dev libssl-dev
```

## Installation:

```
    $ pip install masonite-cli
    $ craft new project
    $ cd project
    $ craft install
    $ craft serve
```

Go to `http://localhost:8000/`

## Contributing

Please read the [Contributing Documentation](https://masoniteframework.gitbook.io/docs/prologue/contributing-guide) here. Development will be on the current releasing branch of the [Core Repository](https://github.com/MasoniteFramework/core) (typically the `develop` branch) so check open issues, the current Milestone and the releases in that repository. Ask any questions you like in the issues so we can have an open discussion about the framework, design decisions and future of the project.

## Contributors

Thank you for those who have contributed to Masonite!

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
| | | |
| :-------------: | :-------------: | :-------------: |
| [<img src="https://avatars.githubusercontent.com/u/6276555?v=3" width="100px;"/><br /><sub><b>Martín Peveri</b></sub>](https://github.com/mapeveri) | [<img src="https://avatars.githubusercontent.com/u/25895176?v=3" width="100px;"/><br /><sub><b>Adorifski</b></sub>](https://github.com/afdolriski) | [<img src="https://avatars.githubusercontent.com/u/1970073?v=3" width="100px;"/><br /><sub><b>Abram C. Isola</b></sub>](https://github.com/aisola) |

## License

The Masonite framework is open-sourced software licensed under the MIT license. 

## Hello World

Getting started is very easy. Below is how you can get a simple Hello World application up and running.

## Installation

You can easily create new applications with `craft`. To create a new application run:

    $ craft new project_name

**NOTE: If you do not have the craft command, you can run `pip install masonite-cli` which will install `craft` and `craft-vendor` command line tools.**

This command will create a new directory called `project_name` with our new Masonite project.

You can now cd into this directory by doing:

    $ cd project_name

Now we just need to add the pip dependencies. You can run `pip3 install -r "requirements.txt"` or you can run the `craft` command:

    $ craft install

**NOTE: Python craft commands are essentially wrappers around common mundane tasks. Read the docs about the craft command tool to learn more**

This will install all the required dependencies to run this framework. Now we can run the `craft` command:

    $ craft serve

This will run the server at `localhost:8000`. Navigating to that URL should show the Masonite welcome message. 

If that port is blocked you can specify a port by running:

    $ craft serve --port 8080

Or specify a host by running:

    $ craft serve --host 192.168.1.283

## Hello World

All web routes are in `routes/web.py`. In this file is already the route to the welcome controller. To start your hello world example just add something like:

```python
Get().route('/hello/world', 'HelloWorldController@show'),
```

our routes constant file should now look something like:

```python
ROUTES = [
    Get().route('/', 'WelcomeController@show'),
    Get().route('/hello/world', 'HelloWorldController@show'),
]
```

**NOTE: Notice this new interesting string syntax in our route. This will grant our route access to a controller (which we will create below)**

Since we used a string controller we don't have to import our controller into this file. All imports are done through Masonite on the backend.

You'll notice that we have a reference to the HelloWorldController class which we do not have yet. This framework uses controllers in order to separate the application logic. Controllers can be looked at as the views.py in a Django application. The architectural standard here is 1 controller per file.

In order to make the `HelloWorldController` we can use a `craft` command:

    $ craft controller HelloWorld

This will scaffold the controller for you and put it in `app/http/controllers/HelloWorldController.py`

We will have a `show()` method by default which is the typical method we will use to "show" our views and content.

Inside the `HelloWorldController` we can make our `show` method like this:

```python
def show(self):
    ''' Show Hello World Template '''
    return view('helloworld')
```

As you see above, we are returning a `helloworld` template but we do not have that yet. All templates are in `resources/templates`. We can simply make a file called `helloworld.html` or run the `craft` command:

    $ craft view helloworld

Which will create the `resources/templates/helloworld.html` template for us.

Lastly all templates run through the Jinja2 rendering engine so we can use any Jinja2 code inside our template like:

inside the `resources/views/helloworld.html`

```
{{ 'Hello World' }}
```

Now just run the server:

    $ craft serve

And navigate to `localhost:8000/hello/world` and you will see `Hello World` in your browser.

Happy Crafting!
