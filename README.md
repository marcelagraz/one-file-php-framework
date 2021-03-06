##ONE <i> PHP Minimalist MVC Framework.</i>
Only 1 file (Easy readable, adaptable). Not MVC required. Ready to go.  
Perfect fit in small projects and web services, only use what you need as you want.
####Features:
#####1- Route system (And generator for views)
#####2- Easy and clean manage (GET, POST, PUT) requests
#####3- Native localizations by URL (Available in controller and views)
#####3- Response (+load Views)
#####4- Inspired in Symfony and ExpressJS    
#####5- Zero config

###Add to your project:
1-Install with Composer or download zip:        
```     
composer create-project julces/oneframework
``` 
2- Include the one_framework.php in your project and  add the .htaccess file in the root folder.     
3- Initialize the class, add some routes-action with get. (See the example bellow).    
4- Run listen.
  
```php
//index.php file    
require_once('one_framework.php');  
$app = new OneFramework();      

$app->get('/',function() use ($app){//Action
    echo 'Hello world';     
});     
$app->listen();
```

####MVC style could look like this:
![MVC folders](http://i60.tinypic.com/ne6hhl.png "MVC folders")


```php
// /controllers/main.php    
//Dynamic route with 1 variable in the URL 
$app->get('/book/{id_book}/edit',function($id_book) use ($app){ 
$book = getBook($id_book);
     return $app->Response('view_path.php',array('book' => $book));
});     
```
####Match a Route if and only is a POST request 
```php
//Action that only run with a POST request
$app->post('/book/{id_book}/update',function() use ($app){
    //save...
});
```
####View and translation
```php
// /views/home.php
// $app is pass as global variable to every View file
 <p>
    <?php echo $app->trans('home_tittle'); ?>
 </p>
```
The framework $app is globally accesible from any view loaded by Response().
#### Translation file look like this
```txt
// /translations/home.en.txt
home_tittle: My website Title
home_menu: Menu
```
Every file inside /translations/ folder will be loaded automatically.
######If you want to see the  /index.php/ in all URLS change the defined constant: <i> APP_NAME</i> in the Framework class and delete the .htaccess from the project.   
*Fell free to change everything you need and make a commit if you improve something.  

[Follow me @juliomatcom](https://twitter.com/juliomatcom    "Follow me and get in touch")  
[http://oneframework.julces.com/](http://oneframework.julces.com/    "Official website")
