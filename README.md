## Laravel Project in Docker Environment

Laravel is a web application framework. Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker's methodologies for developing, testing, and deploying source code, you can significantly reduce the delay between writing code and deployment the application in production. Docker provides tools and a platform to manage the lifecycle of your containers:

- Develop your application and its supporting components using containers and container image.
- The container becomes the unit for distributing and testing your application.
- When you're ready, deploy your application into your production environment, as a container or an orchestrated service. This works the same whether your production environment is a local data center, a cloud provider, or a hybrid of the two.

### Steps of run laravel project in Docker Environment
First of all if you use windows machine then you have to install docker desktop version on windows machine and also windows subsystem linux and some basic configuration for WSL environment in windows machine. you can see this tutorial https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers
after making environment open you window terminal and type below command and hit enter to open ubuntu terminal
```
ubuntu
```

After enter into ubuntu environment using terminal then use below command for crating laravel project project.
```
curl -s "https://laravel.build/your_project_name" | bash
```


after creating laravel project use cd command to go in your project environment usingn this command
`
cd your_project_name
`

Now you can use below command to run you laravel project in docker environment 
```
./vendor/bin/sail up 
or
./vendor/bin/sail up -d
```

If every thing ok then after execute above command you laravel project will run and you can search address of http://127.0.0.1 You might be need file permission to run your project if you get permission denied type error 
`The stream or file "/var/www/html/storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied`
In this case you have to provide ubuntu user permission for your project by running this command.

```
With user root:root . You try with command :

sudo chmod -R 777 storage/

With user www-data:www-data . You try with command :

sudo chown -R www-data:www-data storage/

sudo chmod -R 755 storage/

If you use Docker . You try with command :

sudo chown -R nginx:nginx storage/

sudo chmod -R 755 storage/
```


By default, to run Sail commands, the line <b> "vendor/bin/sail" </b> should precede the commands. We can, however, configure a bash alias that’s just one word to make our commands shorter.

Basically, we’ll replace the line vendor/bin/sail with a word sail:
```
alias sail='bash vendor/bin/sail'
```
To run all the containers in our docker-compose.yml file and get our application started, we use the following command:

```
sail up
```

To start the containers in the background, we use:

```
sail up -d
```




## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
