># Mixpost setup in Local machine

---

## If you are using windows then use `WSL` command to run the following commands  

#### Open the Command prompt Get into Directory where you need to insall a mixpost in you local machine and run

```
WSL --install 
```

Restart the system

After restarting open the `CMD` and get into the directory like C drive or D drive  

```
WSL
```

It will ask password for to login as a root user in Ubuntu machine

Once done with Ubuntu installation run the following commands

># **Requirements**
>
- ## **Software**

  1. For Mixpost the version of PHP >= 8.2.0

   ```
   sudo apt update
   sudo apt install php libapache2-mod-php -y
  ```

    The above  command installs PHP and the Apache PHP module (libapache2-mod-php), which enables Apache to handle PHP files

  2. Installing  Maria Database

   ```
    sudo apt install mariadb-server -y
   ```

  3. Installing Web Server (Apache)

   ```
   sudo apt install apache2 -y
   ```

  4. Installing Supervisor , FFmpeg , Redis 6.2 or higher

   ```
   sudo apt install redis-server supervisor ffmpeg -y
   ```

  5. Installing Composer -y

   ```
   sudo apt install composer
   ```

  6. Installing  Curl , Zip ,  Unzip 

  ```
  sudo apt install zip unzip curl -y
  ```

- ## **PHP Extension**

   Installing php extenstion like `curl`, `mysql`,   `bcmath`,`gd` ,`mbstring`, `redis`, `xml`,`zip`, `intl`

    ```
    sudo apt install php8.3-curl php8.3-mysql php8.3-bcmath php8.3-gd php8.3-mbstring php8.3-redis php8.3-xml php8.3-zip php8.3-intl

    ```

> # Steps to install mixpost

## Step 1 : **Creating the application**

Open CMD and get into the directory In C drive or D drive run the following commands

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

Get into a mysql and set a username & password

In `Password`  you can modify the with your own value

  ```
  mysql 

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
  php artisan serve
  ```
## Step 6 : **Access Mixpost**

Navigate to `http://127.0.0.1:5000`  and the mixpost should appear with the login screen.
