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
$ mkdir -p grails-app/domain/demo/blog/
$ cat > grails-app/domain/demo/blog/Commenter.groovy
> package demo.blog
>
> class Commenter {
>   String addr;
>   String toString() { addr }
> }
> ^D
$ cat >> grails-app/conf/Config.groovy
> import demo.blog.Commenter
> grails.commentable.poster.evaluator = { Commenter.findByAddr(request.remoteAddr) ?: new Commenter(addr: request.remoteAddr).save() }
> ^D
$ git commit -m "Configured commentable plugin to use remote IP as commenter's ID
> 
> Had to create Commenter model as commentable require a persistent poster entity"
