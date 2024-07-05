># Mixpost setup in Cloud Deployment
--- 
   Mixpost is a robust and versatile social media management software, designed to streamline social media operations and enhance content marketing strategies 

   Before getting into a setup there are some Prerequisite 

># **Requirements**

- ## **Software**

1. Installing `PHP >= 8.2.0 `, `maria-db` ,` Web Server `, `composer`
   ```
   sudo apt update 
   sudo apt install php libapache2-mod-php apache2 composer mariadb-server -y
   ```
2. Installing `Supervisor` , `FFmpeg `, `Redis 6.2 or higher`
   
   ```
   sudo apt install redis-server supervisor ffmpeg -y
   ```
3. Installing  `Curl` , `Zip `,  `Unzip`

  ```
  sudo apt install zip unzip curl -y
  ```
- ## **PHP Extension**

 Installing php extenstion like `curl`, `mysql`,   `bcmath`,`gd` ,`mbstring`, `redis`, `xml`,`zip`, `intl`


    sudo apt install php8.3-curl php8.3-mysql php8.3-bcmath php8.3-gd php8.3-mbstring php8.3-redis php8.3-xml php8.3-zip php8.3-intl -y

> # Steps to install mixpost

## Step 1 : **Clone the repository from github**

Open CMD and get into the directory In C drive or D drive run the following commands

Install a composer 

   ```
   cd MixpostApp
   composer install
   ```
## Step 2 : **Setting up .env file**
Get into a maria-db and set a  `password`

  ```
  mysql 

  ALTER USER 'root'@'localhost' IDENTIFIED BY '<Password>';

  exit
  ```
Copy the `.env.example` file and create `.env` file Adjust the  file settings to match your project requirements like `DB_DATABASE`, `DB_USERNAME` , `DB_PASSWORD` , `APP_DEBUG`, `APP_URL` change into `<http://localhost>`

In `Password`  you can modify the with your own value
  ```
  sudo nano .env 
  ```

## Step 3 : **Installing Dependency**

  ```
  sudo php artisan key:generate --ansi
  sudo php artisan mixpost:setup-gitignore
  sudo php artisan queue:batches-table
  sudo php artisan mixpost:publish
  sudo php artisan storage:link
  ```

## Step 4 : **File Permissions**

Get into the mixpostapp directory and Change the file permission

  ```
  cd mixpostapp
  chmod -R 755 public
  chmod -R 775 storage
  chmod -R 775 bootstrap/cache
  ```

## Step 5:  **Application Configuration**

**Optimize application**

  ```
  php artisan optimize
  ```

**Migrate tables**

  ```
  php artisan migrate
  ```

## Step 6 : **Create the first user**

You can create an initial user by executing

  ```
  php artisan mixpost-auth:create
  ```

## Step 7: **Start the server**

 The below Comment  will generate a url open through browser

  Using `Email Id` and `password` login into a mixpost which you provided before the step

  ```
  php artisan serve
  ```
## Step 8 : **Access Mixpost**

Navigate to `http://127.0.0.1:5000`  and the mixpost should appear with the login screen.
