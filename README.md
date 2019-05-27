# social-core
This is about how to use https://github.com/python-social-auth/social-app-flask 

prepare client id and client secret, reference this page: https://simpleisbetterthancomplex.com/tutorial/2016/10/24/how-to-add-social-login-to-django.html

1. install packages
    1.1 install social-auth-app-flask
      $ pip install social-auth-app-flask

    1.2  there are 3 storage solutions, I choose social-auth-app-flask-sqlalchemy
      $ pip install social-auth-app-flask-sqlalchemy
    
2. create app.py

    from social_flask.routes import social_auth
    from social_flask.utils import DEFAULTS

    from flask import Flask

    app = Flask(__name__)
    app.register_blueprint(social_auth)
    
    app.secret_key = 'super secret string'  # Change this!
    
    app.config["KEY"] = 'your client id' # Change this!
    
    app.config["SECRET"] = 'your client secret' # Change this!

    DEFAULTS['AUTHENTICATION_BACKENDS'] = ['social_core.backends.github.GithubOAuth2']


    if __name__ == '__main__':
       app.run(debug = True)
       
 3. execute app.py to see what will come up when enter "http://localhost:5000/login/github/" in the browser
    $ python app.py
 
    You will be directed to github login page, after you enter you credential, you will redirect to another page which is         specified when creating client id and client secret
 
