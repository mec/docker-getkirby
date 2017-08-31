## What is Kirby
Awesome flat file CMS.

Kirby is not free, you can develop locally with Docker and then when you move to production you must purchase a license – support great software!

[https://getkirby.com/](https://getkirby.com/)

## What is the Starterkit

[https://github.com/getkirby/starterkit](https://github.com/getkirby/starterkit)

## How to use this image
To quickly launch and use the image on port 80:

`$ docker run --name my-kirby-project -p 80:80 -d mecrawlings/getkirby-starterkit`

If you want to work on a project or keep any changes you need to mount some directories:

```
$  docker run -d --rm -p 80:80 --name kirby2 \
-v /full/path/to/content:/var/www/localhost/htdocs/content/ \
-v /full/path/to/content:/var/www/localhost/htdocs/site/ \
-v /full/path/to/content:/var/www/localhost/htdocs/assets/ \
mecrawlings/kirby-plainkit
```

The three Kirby directories need to have the content inside them!

You can make this much simpler by…

## …using docker-compose
By using docker-compose you can save yourself loads of typing, I like to create a project folder and add the `docker-compose.yml` like this:

```
version: '2'
services:
  kirby:
    image: mecrawlings/getkirby-starterkit
    volumes:
      - ./content:/var/www/html/content
      - ./site:/var/www/html/site
      - ./assets:/var/www/html/assets
    ports:
      - 80:80
```

Then just run docker-compose up from your project and your up and running. Changes made to the content, site or assets folder will persist.

I keep an up-to-date Kirby-Docker-compose project on github:

[https://github.com/mec/getkirby-base](https://github.com/mec/getkirby-base)
