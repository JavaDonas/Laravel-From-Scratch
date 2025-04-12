# 1 - Deploy With Laravel Forge

Alright, so our application is complete, at least for now. Of ofcourse you can add to it if you want. We're going to do a full deployment and we're going to use a tool called Laravel Forge, which is in my opinion, the easiest way to bring a Laravel site to production. There is something called Laravel Cloud that is going to be released soon and it's supposebly even easier, but for now we'll use Forge along with Digital Ocean cloud hosting. 

We first need to push to Github if you haven't already. Once we setup our Forge server and Digital Ocean droplet, we're going to add a domain name. I'll be using workopia.dev but you can use your own domain. Then we'll add a free SSL certificate via Let's Encrypt. We can do this with a single click in Forge. Then we'll test everything out and we should be all set.


# 3 - Push To Github

We will bew using Laravel Forge and Digital Ocean to deploy our application. In order to get the files onto the server, we need to push our code to Github. Many of you probably already have done this, but if you haven't, here is how you do it.

## Disable Mailing

Since I did not go through the Mailtrap compliance yet, I'm going to disable the sending of emails when a user applys to a job. Open the `app/Http/controllers/ApplicantController.php` and comment out the following line:

```php
// Mail::to($job->user->email)->send(new JobApplied($application, $job));
```

After you do the compliance form, you can uncomment the line again.

I would also suggest adding the following line to your .gitignore file to prevent the theme_files from pushing to your repo:

```
/_theme_files
```

## Push To Github

If you have not created a Github account yet, you can do so here: https://github.com/

Initialize a git repository in your project folder if you have not done so already.

```bash
git init
```

Add the files to the repository.

```bash
git add .
```

Commit the files.

```bash
git commit -m "Initial commit"
```

Create a new repository on Github.

Go to the repository settings and copy the URL.

```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

Push the files to Github.

```bash
git push -u origin main
```

Now your files should be on Github and we are ready to move to the next step.


# 3 - Setup Laravel Forge

There are a lot of ways to deploy a Laravel project. Unfortunately, many of them are pretty difficult, especially if you are coming from a frontend development background.

## What is Laravel Forge?

Laravel Forge is a server management tool that makes it easy to deploy Laravel applications. It takes care of setting up your enviroment with everything from PHP to NGINX to your database. It is a paid service, but it is worth it. You can chose the "Hobby" plan for $12 per month. I really wanted to find a free solution for you guys, but the reality is that none really exist.

Forge itself does not host your application. It is just a tool that makes it easy to deploy your application to a server. You can use it with any server, but it is most commonly used with Digital Ocean and AWS. I prefer Digital Ocean because it is cheaper and easier to work with in my opinion.

You can use something like Digital Ocean, Linode or AWS on their own without Forge, but that is a lot of work to set up. There is a lot of provisioning that needs to be done and you really need to understand Lunux and the terminal. You need to manually install and configure all the software you need and you're almost guaranteed to run into issues unless you're really experienced.

## Create Server

You will need an account for both Forge and Digital Ocean. Let's head to https://forge.laravel.com/ and sign up for an account. Log in and you will see the dashboard. From here, you can create a new server.

You have a bunch of hosting options to choose from. I am going to use Digital Ocean. It will take you through the process of setting up your digital ocean account if you don't have one already.

Choose the pre-selected "App Server" option. You can leave the defaults for the rest as well. Click "Create Server".

<img src="../images/forge.png" alt="" />

It will show your sudo/ssh password and database password. Copy those and put them somewhere. It will take up to 10 - 15 minutes to set everything up.

## Create Site

Once you create a server, you can then create a site.

There will be a "default" site created already and that is what the public domain points to. You can use that if you want to access the site with the IP address. I am doing a full deployment with a domain and SSL, so I am going to use the "New Site" option and add my domain name.

<img src="../images/forge2.png" alt="" />

Now select "Git Repository" and enter the URL of your Laravel app repo. Select the "main" branch.

You can choose the database name. Forge uses MySQL and I know we used Postgres in development, but it really doesn't matter because all of our code stays the exact same. The only difference is the .env config values, which Forge will update for us.

Click "Install Repository".

## Edit Deployment Script

Before we deploy, we need to edit the deployment script. This already includes things like running our migrations but we need to add a few things. Click on the "Edit Files" button and select "Edit Deployment Script". Add the following lines to the end of the script:

```bash
php artisan storage:link

npm install

npm run build
```

<img src="../images/forge3.png" alt="" />

This will add our storage link, install the dependencies and run the build the frontend assets.

## Edit .env

Click the "Edit Files" button and select "Edit .env".

Add the following value at the bottom of the file:

```bash
MAPBOX_API_KEY=YOUR_API_KEY
```

If you plan on using mailing with Mailtrap, then also add your Mailtrap password and from email address.

Save the file.

Select "Make .env available to script" and click "Save".

Now, Deploy the project.

Once it says "Active", the project is deployed, but it is still not accessible because we need to setup the domain. We will do that next.


# 4 - Add Domain Name

Now that our server is setup on Forge & Digital Ocean, we need to setup the domain name. Go to the registrar of wherever you bought your domain name and add the Digital Ocean nameservers. This is so we can manage the domain via Digital Ocean.

Here are the nameservers:

- ns1.digitalocean.com
- ns2.digitalocean.com
- ns3.digitalocean.com


Now go to Digital Ocean and select "Add Domain" for your droplet. Type in the doman and select the droplet.

This will create the A record that we need. Now you just need to add a CNAME for the following:

- www: yourdomain.com

Next, we need to setup the SSL on Forge.


# 5 - SSL & Launch Test

Now we need to add an SSL. We can get a free SSL with Let's Encrypt via the Forge interface. Log into Forge and click on "SSL". Select "Let's Encrypt". It will take a minute or so and then it should say active.

Now go to your domain name in the browser and it should work. If it doesn't just wait a while. It can take anywhere from a few minutes to 48 hours, but it is usually very quick.

Now just go through and test the following:

- Register user
- Login user
- Upload an avatar
- Add a job listing
- Edit listing
- Bookmark listing
- View saved listings
- Remove bookmark
- Apply and upload resume
- View appllicants on dashboard
- Delete applicant
- Delete job listing
- Log out

That's it! Our application is done and deployed.


# 6 - Wrap Up

Alright guys, I really hope that you enjoyed this course. I tried to include as much as I could and fit it into a single project. We learned all about routes, controllers, views, components, models, migrations and the list goes on. My advice now is to take what you've learned and use those skills to create some more of your own projects. Courses and tutorials can only help you so much. Getting into the weeds and figuring something out on your own from start to finish is one of the most valuable things that you can do in your learning experience.

Once you feel ready you can move on to either applying for positions or start taking clients, or build a product like a SaaS. Whatever it is you learn Laravel to be able to do. 

Move on to learn about other tools in the Laravel ecosystem as well. Before you know it you'll be a pro.

Thanks so much for taking this course guys. I really appreciate it and I hope you enjoyed it and found it fulfiling. See you in the next course.