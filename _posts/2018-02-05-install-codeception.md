---
layout: single
title:  "Hướng dẫn cài đặt CodeCeption"
desc: "Hướng dẫn cài đặt CodeCeption"
excerpt: "Hướng dẫn cài đặt CodeCeption"
keywords: "test, codeception"
categories: [technology]
tag: [test, codeception]
---

Codeception install

### 1. Install wamp to get php
	add php to environment
	
### 2. install composer
	`https://getcomposer.org/download/`
	
### 3. install codeception
 > cd lib/folder
 > composer require "codeception/codeception" --dev

	This will download all data of this Codeception library
	The main source is in folder:
		`..\vendor\codeception\codeception\src\Codeception`
 
## I. On window 
 
### 4. Create test code 
```
 > cd project/path
 > ../vendor/bin/codecept bootstrap
 
```

 This will create folder tests and file `codeception.yml`
 

## II. On linux

### 4. Create test code 
	**a. copy folder Codeception (bao gồm folder `vendor` và file `composer.json`)**
	vào thư mục `/usr/local`
	
	**b. Cấp quyền run cho file chạy**
	> sudo chmod +x /usr/local/Codeception/vendor/bin/codecept
	> chmod +x /usr/local/Codeception/vendor/codeception/codeception/codecept
	
	**c. tạo test code**
	```
	> cd project/path
	> sh /usr/local/Codeception/vendor/bin/codecept bootstrap
	```
	
	This will create folder `tests` and file `codeception.yml` in the same folder with application, ...
	
	**d. Add library to php.ini to dynamic call**
```
		> vi /usr/local/lib/php.ini
		include_path = ".:/usr/local/lib/php/:/usr/local/lib/php/PEAR"
to 		include_path = ".:/usr/local/lib/php/:/usr/local/lib/php/PEAR:/usr/local/Codeception/vendor/codeception/codeception/src/Codeception"
```
