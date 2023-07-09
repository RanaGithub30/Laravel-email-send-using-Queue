## Send Email Using Laravel Queue

# Why Queue?

   - Sometimes, you see some processes take time to load like email send, payment gateway, etc. When you send an email for verification or send an invoice then it loads time to send mail because it is services. If you don't want to wait for the user to send an email or other process on loading server-side process then you can use a queue. because it's very fast and visitors will happy to see loading time.

## Step by step process

   - Install laravel project using following command

             composer create-project laravel/laravel:^9.0 example-app

   - we will create email for testing using Laravel Mail facade. So let's simple run bellow command & copy bellow code and past on that file.

             php artisan make:mail SendEmailTest

   - Now we require to create email view using blade file. So we will create simple view file and copy bellow code om following path.
   - After configuration of view file, we have to setup for email send, So let' set configuration in .env file
   - Now in next step, we will make configuration on queue driver so first of all, we will set queue driver "database". You can set as you want also we will define driver as Redis too. So here define database driver on ".env" file

            QUEUE_CONNECTION=database

   - After that we need to generate migration and create tables for queue. So let's run bellow command for queue database tables

            a) php artisan queue:table
            b) php artisan migrate

   - Now we will create queue job by following command, this command will create queue job file with Queueable. So let's run bellow command

            php artisan make:job SendEmailJob

   - now you have SendEmailJob.php file in "Jobs" directory. So let's see that file and put bellow code on that file.
   - Now create a route to execute the email send functionality
   - Next, you must have to run following command to see queue process, you must have to keep start this command

            php artisan queue:work

   - All the required steps have been done, now you have to type the given below command and hit enter to run the Laravel app

            php artisan serve

   - Now, Go to your web browser, type the given URL and view the app output
           
            http://127.0.0.1:8000/email-test