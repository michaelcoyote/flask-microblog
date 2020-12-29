## Flask microblog

Just an implementation of [Miguel Grinberg's Flask based microblog](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world).  You can use this but you're better off just going through the exercises yourself. I may have made changes

This is probably out of date and there might be better ways to learn Flask, but
this exercise has been pretty solid and no overt errors in the code so far.


### Random useful things documented here

Basically so I don't have to dig through docs to look this up later

#### Setting up error mailing

This is in [Chapter 7](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-vii-error-handling) along with error pages.

Use these environment variables to send errors through gmail:
```bash
export MAIL_SERVER=smtp.googlemail.com
export MAIL_PORT=587
export MAIL_USE_TLS=1
export MAIL_USERNAME=<your-gmail-username>
export MAIL_PASSWORD=<your-gmail-password>
```



### Notes to myself/documentation

Currently on [chapter 8](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-viii-followers)

#### Things to do before checking in

1. Save the pip requirements `pip freeze > requirements.txt`
2. Update the current chapter in the readme

