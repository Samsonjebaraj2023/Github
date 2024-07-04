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

## Step 1 : **Creating the application**

  ```
   composer create-project inovector/MixpostApp
   ```

## Step 2 : **File Permissions**

Get into the mixpostapp directory and Change the file permission

  ```
  cd mixpostapp
  chmod -R 755 public
  chmod -R 775 storage
  chmod -R 775 bootstrap/cache
  ```
## Step 3 :  **Application Configuration** 

Get into a mariadb and set a username & password

In `Password`  you can modify the with your own value

  ```
  sudo mysql 
  ALTER USER 'root'@'localhost' IDENTIFIED BY '<Password>';
  exit
  ```
Adjust the `.env` file settings to match your project requirements like `DB_DATABASE`, `DB_USERNAME` , `DB_PASSWORD` , `APP_DEBUG`, `APP_URL` change into `<http://localhost>`
```
  sudo nano .env
  ```

  **Optimize application**

  ```
  php artisan optimize
  ```

**Migrate tables**

  ```
  php artisan migrate
  ```
## Step 4 : **Create the first user**

You can create an initial user by executing

  ```
  php artisan mixpost-auth:create
  ```
## Step 5 : **Start the server**

 The below Comment  will generate a url open through browser

  Using `Email Id` and `password` login into a mixpost which you provided before the step

  ```
  php artisan serve --host=0.0.0.0 --port=8000
  ```
## Step 6 : **Access Mixpost**

Navigate to `http://<EC2_INSTANCE_IP>:8000`  and the mixpost should appear with the login screen.
