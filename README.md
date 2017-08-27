In the video: Build and deploy rails app in less than 4 minutes, we use Cloud9 to instantly install Ruby and Ruby on Rails on a virtual Linux server in the cloud. We very quickly create a rough and simple web application using the Rails scaffolding generator.

We' use GIT for version control, and we push our work up to Github, so that we can share our code, and finally, we deploy our application to production by pushing it up to Heroku.

From nothing, to deployed web application in less than 4 minutes. Obviously not a finished and polished application, but enough for you to get the idea.

Here’s what we did:


1) Go to Cloud 9 www.c9.io  (sign up for a free account)
	a)  Click on “Create a new workspace”
	b)  Choose the Ruby on Rails Template
	c)  Click on the Create Workspace button

2) Open the Gem file and make these changes
	a)  Move:
       		gem 'sqlite3' (to under group :development, :test do)

	b) Add to bottom:
        group :production do
            gem 'pg'
            gem 'rails_12factor'
        end
  
3)  In the Cloud9 terminal enter:
	a)  bundle install –without production
	b)  rails g scaffold News title:string article:text
	c)  rake db:migrate

4)  Go to Config > Routes
	un-comment the root route and change route to:   root ‘news#index’

5)  In the Cloud9 terminal enter:
	rails server -b $IP -p $PORT (to start the rails server on Cloud9’s virtual local host and view in browser)

6)  Check it out and add some articles

7) In the Cloud9 terminal enter:
	a)  git init  (to initialize a new git repository for version control)
	b)  git add -A   (to add your code to git)
	c)  git commit -m "initial commit" (to commit your code with a message)

8)  go to Github and click on "New Repository"  (sign up for free account)
	fast-news

9)  In the Cloud9 terminal enter:
	a)  git remote add origin git@github.com:chris-intelatek/fast-news.git
	b)  git push -u origin master

10)  Go to heroku.com (create account)
	a)  click on "New"
	b)  Enter your new app name (must be unique)

11)  In the Cloud9 terminal enter:  
	a)  heroku login
	b)  enter your heroku account email
	c)  enter your heroku account password
	d)  heroku git:clone -a app-name
	e)  git push heroku master
	f)  heroku run rake db:migrate

12)  Click on open app button on heroku to view deployed app in browser

13)  Check it out and add some articles
