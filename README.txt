$ grails create-app grails-blog
$ cd grails-blog
$ git init
$ cat >> .gitignore
> /.classpath
> /.project
> /.settings
> /web-app/WEB-INF
> /target
> ^D
$ git commit -m "Importing vanilla Grails app (withoug eclipse crap!)"
