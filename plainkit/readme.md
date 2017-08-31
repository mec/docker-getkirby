## What is Kirby
Awesome flat file CMS.

Kirby is not free, you can develop locally with Docker and then when you move to production you must purchase a license – support great software!

[https://getkirby.com/](https://getkirby.com/)

### What is the Plainkit

[https://github.com/getkirby/plainkit](https://github.com/getkirby/plainkit)

## How to use this image
To quickly launch and use the image:

`$ docker run --name my-kirby-project -p 80:80 -d mecrawlings/getkirby-plainkit`

If you want to work on a project or keep any changes you need to mount some directories:

`$ docker run --name my-kirby-project -p 80:80 -d mecrawlings/getkirby-plainkit -v <fullpathto>/content -v <fullpathto>/site -v <fullpathto>/assets`

You can make this much simpler by…

## …using docker-compose
By using docker-compose you can save yourself loads of typing, I like to create a project folder and add the `docker-compose.yml` like this:

```
version: '2'
services:
  kirby:
    image: mecrawlings/getkirby-plainkit
    volumes:
      - ./content:/var/www/html/content
      - ./site:/var/www/html/site
      - ./assets:/var/www/html/assets
    ports:
      - 80:80
```
Then just run `docker-compose up` from your project and your up and running. Changes made to the content, site or assets folder will persist.

I keep an up-to-date Kirby-Docker-compose project on github:

[https://getkirby.com/](https://getkirby.com/)
