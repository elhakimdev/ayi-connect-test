## About
Aplikasi ini sudah di bundle denngan laravel sail (docker dev env), dann jetstream. sehingga tidak memerlukan konifgurasi database maupun versi php / node js , cukup tinggal jalankan perintah sail maka applikasi akann berjalan.

- Laravel Sail = https://laravel.com/docs/9.x/sail

## How To Run (WITH DOCKER/SAIL)
- clone repo ini ke local, setelah proses clone selesai, masuk ke directory hasil clone tadi
- jalankan command ```cp .env.example .env``` untuk meng-copy .env.example => .env
- setelaah itu buka file .env
- ganti bagian database config menjadi 
```DB_HOST=mysql```, 
```DB_PASSWORD=password```,
```DB_PORT=3306```, 
```DB_USER=sail```, 
```DB_DATABASE=ayi_connect``` sesuaikan dengan port yang anda inginkan,, pastiikan port yang di pakai tidak beentrok denngan port yang di pakai di applikasi lain. 
- jalankan perintah ```composer install --ignore-platform-reqs```, atau lebih di sarankan menjalanakan composer dari docker image, dengan cara ```docker run --rm --interactive --tty --volume $PWD:/app composer --ignore-platform-reqs```,
- setelaah itu cek apakah laravel + sail udah terinstall denngan cara ```./vendor/bin/sail```
- langkah trerkahir jalankan container dengan cara ```./vendor/bin/sail up -d```

- setelaah container berjalan, jalankan perintaah dibawah ini berurutan
-```./vendor/bin/sail artisan key:generate```
-```./vendor/bin/sail artisan migrate```
-```./vendor/bin/sail npm install```
-```./vendor/bin/sail npm run build```


- untuk mengganti localization/bahasa app. tinggal ganti di ```config/app.php``` di bagian app_locale sesuai dengan yang di inginkan, default = en , avail = en, es, id,
- untuk menjalankan unit test, bisa dengan command ```./vendor/bin/sail artisan test```