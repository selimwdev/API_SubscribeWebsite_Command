# API_SubscribeWebsite_Command

**Installation**
````
Download https://drive.google.com/file/d/15xri222n-xKvY6gBqzo5fh3HmSHoeG8h/view?usp=sharing
composer update
composer install
php artisan key:genrate
Edit .env file to provide necessary config
php artisan migrate
php artisan db:seed
````

**Start the server**

````php artisan serve````

**Show data**
````
GET http://127.0.0.1:8080/websites (show all websites)
GET http://127.0.0.1:8080/websites?page=1
GET http://127.0.0.1:8080/websites?page=2
GET http://127.0.0.1:8080/websites/1 (show website 1)
GET http://127.0.0.1:8080/websites/1/posts (show posts on website 1)

GET http://127.0.0.1:8080/posts (show all posts)
GET http://127.0.0.1:8080/posts?page=1
GET http://127.0.0.1:8080/posts?page=2
GET http://127.0.0.1:8080/posts/1 (show post 1)

GET http://127.0.0.1:8080/subscribes (show all subscribes)
GET http://127.0.0.1:8080/subscribes?page=1
GET http://127.0.0.1:8080/subscribes?page=2
GET http://127.0.0.1:8080/subscribes/1 (show subscribe 1)
````


**Create post/website**
````
POST http://127.0.0.1:8080/websites

{
    "title":"Website 1",
    "url":"example.com"
}
````

````
POST http://127.0.0.1:8080/posts
{
    "title":"Post 1",
    "description":"hello world",
    "website_id":1
}
````


**Update post&website**

````
PATCH http://127.0.0.1:8080/websites/1

{
    "title":"new Website 1",
    "url":"example.com"
}
````

````
PATCH http://127.0.0.1:8080/posts/1
{
    "title":"new Post 1",
    "description":"hello world",
    "website_id":1
}
````

**Delete post&website&subscribes**

````
DELETE http://127.0.0.1:8080/websites/1

DELETE http://127.0.0.1:8080/posts/1

DELETE http://127.0.0.1:8080/subscribes/1
````


**Subscribe website**

````
POST http://127.0.0.1:8080/subscribes
{
     "email":"mohamed@selimdev.com",
     "website_id":1
}
````


**Send mails when subscribe && create new post (commands)**

````
php artisan queue:listen
php artisan posts:notify
````
