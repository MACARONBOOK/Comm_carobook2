# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# Comm_carobooks<br>
 create group / send_mail_function on them.
 
 ## group_function
 * create controller(groups)<br>
 
 * create 2model (group / group_user)<br>
 
 * association with 3model(user - group_user<stock table> - group)<br>
 
 * add routing<br>
 
 * add link on users/index<br>
 
 * write views<br>
 
 * edit migration-file<br>
   rails db:migrate:status → check up and down(is there saved?)<br>
   rails db:rollback STEP=2 → this case rollback recent-2file.<br>
   edit existing-file<br>
   rails db:migrate → can all migrate by one-action
 
 * add action(join/update/destroy) on groupCon

## send_mail_function
 * create mailer → can use ActionMailer by Ruby on Rails<br>
   rails generate mailer ContactMailer
 
 * add mailer-format on config/environments/development.rb(above end)<br>
   config.action_mailer.raise_delivery_errors = true<br>
   config.action_mailer.delivery_method = :smtp<br>
   config.action_mailer.smtp_settings = {<br>
    port:                 587,<br>
    address:              'smtp.gmail.com',<br>
    domain:               'gmail.com',<br>
    user_name:            'YOUR_ADDRESS',<br>
    password:             'PASSWORD',<br>
    authentication:       'login',<br>
    enable_starttls_auto: true<br>
  }
  
  * write on application_mailer.rb<br>
    default from: '○○○○<from@gmail.com>'<br>
    layout 'mailer'
    
  * add function on groupsCon<br>
    def new_mail<br>
    @group = Group.find(params[:group_id])<br>
  end<br>

  def send_mail<br>
    @group = Group.find(params[:group_id])<br>
    group_users = @group.users<br>
    @mail_title = params[:mail_title]<br>
    @mail_content = params[:mail_content]<br>
    ContactMailer.send_mail(@mail_title, @mail_content,group_users).deliver<br>
  end
  
  * create new view(contact_mailer/send_mail)
  
  * add routing(route of groups#new_mail & groups#send_mail)
  
  * edit contact_mailer.rb<br>
    def send_mail(mail_title,mail_content,group_users) #set argument to method<br>
     @mail_title = mail_title<br>
     @mail_content = mail_content<br>
     mail bcc: group_users.pluck(:email), subject: mail_title<br>
    end
  
  ## gem_dotenv-rails<br>
  * add to Gemfile<br>
    gem 'dotenv-rails'<br>
    →bundle install
  
  * create new-file(.env) on same line with Gemfile
  * write on .env<br>
    KEY='ki.abcdfgh@gmail.com'    ←address of gmail<br>
    SECRET_KEY='abcdefsgsdhsgjd'  ←app_password
    
  * add on .gitignore<br>
    /.env    ←not reflected to GitHub
    
    
