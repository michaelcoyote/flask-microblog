## Flask microblog

Just an implementation of [Miguel Grinberg's Flask based microblog](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world).
You can use this code but you're better off just going through the exercises yourself. 

I may have made changes, use at your own risk.

This is probably out of date and there might be better ways to learn Flask, but
this exercise has been pretty solid and no overt errors in the code so far. I
do sometimes have issues understanding where new code should be placed and I
find it useful to go check out the [example repo on GitHub](https://github.com/miguelgrinberg/microblog).
All chapters are tagged on the example repo for easy reference.

I've made some changes to formatting and have converted to use f-strings where
it makes code more readable.


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

To test email you can run a test mail server using python:

```bash
python -m smtpd -n -c DebuggingServer localhost:8025
```

You can then configure the webapp to use this server by setting the following
variables:
```bash
export MAIL_SERVER=localhost
export MAIL_PORT=8025
```

#### Unit tests
In [Ch. 8](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-viii-followers/page/0#comments)
there are some unittests using the `unittest` framework and can be run with `python tests.py`

#### 

### Notes to myself

Currently on [chapter 10](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-x-email-support)

#### Things to do before checking in

1. Save the pip requirements `pip freeze > requirements.txt`
2. Update the current chapter in the readme

