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
$ grails install-plugin simple-blog
$ git commit -m "Installing simple-blog plugin with depns"
$ cat >> grails-app/conf/Config.groovy
> grails.blog.author.evaluator = { request.remoteAddr }
> ^D
$ git commit -m "Configured simple-blog to use remote IP as posters ID"
