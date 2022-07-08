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
 create group_function on them.
 
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
