# Django_RestAPI
Rest api using django frame work which will store the value of user name, first and last name, password
>>>rest api<<
pip install pipenv
pipenv shell
pipenv install django
django-admin startproject contactsapi
mv all files to contactsapi folder
code . (to open vs code)
python manage.py runserver
http://127.0.0.1:8000/
python manage.py runserver 7500  (changed the port number)
http://127.0.0.1:7500/
pipenv install djangorestframework
setting.py add rest_framework
python manage.py startapp authentication
create serializers.py, url.py files in authentication app
--code changes in views.py
in authentication app edit the views.py file
1)add a class RegisterView() and import test framework generics
2)inside class call genericAPIVIEW and define the function post method
--serializer code changes
1)create a class userserializer with modelserializer and import the rest framework serialzers & django auth models
2)add 4 fields password, email, first_name, last_name (with field data types and max and min length)
3)create a Meta class add the 4 fields password, email, first_name, last_name for the model users
4)create a function for validate if a email is already exist
5)create a function  def create for the validate data 4 fields
--code changes in views.py
1)import restframework userserializer, restframework Response, rest_framework Status
2)Created RegisterView with genericAPIView argument
3)created post method and validated serializer data and gave bad request 201 & 400 for failure
>>>python manage.py migrate
>>>python manage.py runserver 7500
---setting.py
add authentication in Installed apps
--authentication urls.py
1)import django urls and .views
2)add url pattern = register view
--contactapi urls.py
1)import django urls include
2)add an path api/auth authentication.urls
--goto POSTMAN
1)create a collection contactsapi and request name register
2)post request give the URL
3)http://127.0.0.1:7500/api/auth/register
4)body change raw and format JSON
5)give the input for 4 field and fire post request
{
    "username" : "srinivas",
    "first_name": "srinivas",
    "last_name":"raju",
    "password":"raju1234",
    "email":"srinu@gmail.com"
}
---->>>>setting JWT authentication scheme--user login
pipenv install pyjwt
--authentication view.py
1)create a class loginview with function post method
2)Inside post function give 2 fields username and password
--create a backend.py file
1)create JWTauthetication class and deine a function authentication
2)try and except for token
create files .env and .gitignore files in contactsapi folder
--postman
http://127.0.0.1:7500/api/auth/login
>>>python manage.py runserver 7500
--create a app
python manage.py startapp contacts
python manage.py makemigrations
python manage.py migrate
python manage.py runserver 7500
http://127.0.0.1:7500/api/auth/login/

