# Docker Base Image with Pyenv preinstalled

[![tzenderman/docker-pyenv](http://dockeri.co/image/tzenderman/docker-pyenv)](https://registry.hub.docker.com/u/tzenderman/docker-pyenv/)

You probably already version the packages you use in your project, but have you ever run into an issue where you or other developers on your team can't reproduce an issue exactly the way someone else on the dev team is experiencing it? This really grinds my gears, so I made this image to prevent that situation! With this Docker image, you can version even your project's languages to avoid any silly differences between environments.

Docker Hub Link: https://registry.hub.docker.com/u/tzenderman/docker-pyenv/

## Want to use this in your project?

Simply add

`FROM tzenderman/docker-pyenv:latest`

to the top of your Dockerfile and that's it. You'll now have pyenv pre-installed in your container. Want to manage your python version in your project's repo? Simply add `.python-version` to the root of your project next to your project's `Dockerfile`.

And then manage the install inside your project's Dockerfile like this:

    WORKDIR /code

    COPY .python-version /code/.python-version
    COPY requirements.txt /code/requirements.txt
    RUN yes | pyenv install $(cat .python-version) && \
        pip install -r /code/requirements.txt

Now, when you want to upgrade to Python 3.4, simply update your `.python-version` to `3.4.0`, rebuild your Docker image, and that's it!

Links:

Pyenv: https://github.com/yyuu/pyenv
