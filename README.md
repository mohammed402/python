# python
pip install flask_mysql   #in command prompt of python
from flask import Flask,request
from flaskext.mysql import Mysql
mysql=Mysql()
app=Flask(__name__)
app.config['MYSQL_DATABASE_USER']='root'
app.config['MYSQL_DATABASE_PASSWORD']='arifa'
app.config['MYSQL_DATABASE-DB']='Empdata'
app.configg['MYSQL_DATABASE_HOST']='localhost'
mysql.init_app(app)
@app.route("/")
@app.route("/Authenticate")
def Authenticate():
	username=request.args.get('username')
	password=request.args.get('password')
	cursor=mysql.connect().cursor()
	cursor.execute("select * from user where username='"+username+"'+and password='"+password+'")
	data=cursor.fetchone()
	if data is none:
		return "user or paasword is wrong"
	else:
		return "logged in successfully"
