---
title: Cloning a Laravel + Oracle 11g Project Requirements
date: 2022-02-27 07:17:50 +0600
categories: [Backend Development, Laravel8]
tags: [backend development,laravel8,oracle11g]     # TAG names should always be lowercase
author: <author_id> 
toc: false
pin: false
comments: true
---

> php version : 8.0.3 , OS: Windows, System Specification : 64-bit operating system, x64-based processor
{: .prompt-info }

<code class="language-plaintext highlighter-rouge">Step 0</code> Install xampp, laravel from this [link](https://www.apachefriends.org/download.html) and 
[tutorial](https://www.youtube.com/watch?v=fiXdUXy2xjE)

<code class="language-plaintext highlighter-rouge">Step 1</code> Set xampp server

```If Error```: Apache shutdown unexpectedly

```Solution``` : Go to apache config -> httpd.config and Set Listen 80 to Listen 8085

<code class="language-plaintext highlighter-rouge">Step 2</code> Start the apache server and Check whether xampp is working or not: ```http://localhost:8085/dashboard/```

<code class="language-plaintext highlighter-rouge">Step 3</code> Install composer from this [link](https://getcomposer.org/) Or [this link](https://getcomposer.org/download/)
[Helper tutorial](https://www.youtube.com/watch?v=RyYKXyvM3D4)

<code class="language-plaintext highlighter-rouge">Step 4</code> Download php_oci8.dll and php_oci8_11g.dll from 
[here](https://drive.google.com/drive/folders/1geoo4LaZdPwvs0JExdHYEaUJT65QRO6k?usp=sharing)

<code class="language-plaintext highlighter-rouge">Step 5</code> Install Instantclient-basic-nt-12.1.0.2.0.zip from [here](https://www.oracle.com/database/technologies/instant-client/microsoft-windows-32-downloads.html)

<code class="language-plaintext highlighter-rouge">Step 6</code> Copy and paste the php_oci8.dll and php_oci8_11g.dll in C:\xampp\apache\bin and C:\xampp\php\ext

<code class="language-plaintext highlighter-rouge">Step 7</code> Add the two lines in C:\xampp\php\php.ini

```dll
extension=php_oci8.dll  
extension=php_oci8_11g.dll
```

<code class="language-plaintext highlighter-rouge">Step 8</code> Make sure the extension directive is set to
extension_dir ="C:\xampp\php\ext” In php.ini

<code class="language-plaintext highlighter-rouge">Step 9</code> remove ; (uncomment) before extension=fileinfo in php.ini file , if there is already no ; then skip this step.

<code class="language-plaintext highlighter-rouge">Step 10</code> Add path in system variables in this order

```directory
C:\xampp\php
C:\ProgramData\ComposerSetup\bin
C:\xampp\php\instantclient_12_1
```

<code class="language-plaintext highlighter-rouge">Step 11</code> Clone GitHub repo for this project locally.

<code class="language-plaintext highlighter-rouge">Step 12</code> cd into your project

<code class="language-plaintext highlighter-rouge">Step 13</code>Install Composer Dependencies(in cmd write):

```console
composer install
```

<code class="language-plaintext highlighter-rouge">Step 14</code> nstall NPM Dependencies :

```console
npm install
```

<code class="language-plaintext highlighter-rouge">Step 15</code> copy the text in .env.example file in the project directory and paste in A newly created .env file(create an empty .env file manually)

<code class="language-plaintext highlighter-rouge">Step 16</code> write in the cmd to generate a key

```console
php artisan key:generate
```

<code class="language-plaintext highlighter-rouge">Step 17</code> In the .env file edit the database connection information

```console
DB_CONNECTION=oracle
DB_HOST=localhost
DB_PORT=1521
DB_DATABASE=xe
DB_USERNAME=********(your username)
DB_PASSWORD=*********(your password)
```

<code class="language-plaintext highlighter-rouge">Step 18</code> migrate all the tables created in laravel:

```console
php artisan migrate
```

<code class="language-plaintext highlighter-rouge">Step 19</code> If fresh migration needed (dropping all tables, and migrating them freshly):

```console
php artisan migrate:fresh
```

<code class="language-plaintext highlighter-rouge">Step 20</code> to render the project in the browser:

```console
php artisan serve or php artisan serve --port=8081
```
