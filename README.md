# Docker & Kirby

This repo contains my Dockerfiles for both plainkit and starterkit versions of [Kirby CMS](https://getkirby.com).

## Install & use

You can use these images from [Docker hub](https://hub.docker.com), just install [Docker](https://www.docker.com) for your system and them at a command prompt:

``docker run -d -p 80:80 mecrawlings/getkirby-plainkit``

``docker run -d -p 80:80 mecralwings/getkirby-starterkit``

Which will run them in detached mode on port 80, visit:

``http://localhost``

to see the running site.

## Note

The *content*, *site* and *assets* directories are mounted and saved to the file system only as long as the running container exists! To actually develop and keep you changes you must bind mount the host directories at runtime:

``docker run -d -p 80:80 -v /User/kirby-project/content:/var/www/html/content -v ./User/kirby-project/site:/var/www/html/site -v ./User/kirby-project/assets:/var/www/html/assets mecrawlings/getkirby-starterkit``

or use my Docker [getkirby-base](https://github.com/mec/getkirby-base) project which does it for you!
