# LoopClub

The "email" folder is the front-end file written in Vue.js using the Quasar framework and the "Email-Subscription" contains files for backend written in Python/Django which can run as REST APIs

### Steps to follow

1) Download node from official site ```nodejs.org```
2) Run the following commands

Clone the repo

```
git clone https://github.com/mystery2828/LoopClub.git

```

Install packages for frontend
```
npm install -g @quasar/cli
cd email
npm install
quasar dev
```

For running the API

```
cd Email-Subscription
pip install -r requirements.txt
python manage.py runserver
```

### Methods allowed are POST and GET
Use POST method to make a POST request at http://127.0.0.1:8000/ to add the email to the database,
Use GET method to make a GET request without any arguments at http://127.0.0.1:8000/ to get the list of email ids registered

**Use Postman or chrome for easy get request


