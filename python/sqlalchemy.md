# SQLAlchemy with `mysql`

### Install (with virtualenv)
~~~
pip install flask
pip install flask_sqlalchymy
~~~


### ipython 
~~~
pip install ipython
ipython (ipython 실행)
~~~

### Code
> application.py
~~~
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI']='mysql://root:@localhost/<database name>'

db = SQLAlchemy(app)

class User(db.Model):
    id = db.column(db.Integer, primary_key=True)
    username = db.column(db.String(50), nullable=False)
    email = db.column(db.String(100), nullable=False)
    
    def __repr__(self):
        return '<User %r>' % self.username
~~~

### Create Database
~~~
from application import db
db.create_all()
~~~

#### No module named MySQLdb
[stackoverflow](https://stackoverflow.com/questions/454854/no-module-named-mysqldb)
~~~
apt install libmysqlclient-dev
apt install python-mysqldb
pip install mysqlclient
~~~

### Create
~~~
from application import db, User
test = User(username='test', email='test@naver.com')
db.session.add(test)
db.session.commit()
~~~

### Read
~~~
from application import db, User
User.query.all() (모든)
User.query.get(1) (id가 1번인)
~~~

### Update
~~~
from application import db, User
test = User.query.first()
test.email (이메일정보확인)
test.email = 'test@gmail.com' (이메일수정)
db.session.commit()
~~~

### Delete
~~~
from application import db, User
test = User.query.get(1) (id = 1 -> test)
test (test 내용 확인)
db.session.delete(test)
User.query.all() (삭제되었나 확인)
db.session.commit() (커밋)
~~~

###
~~~
~~~
