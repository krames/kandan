In order to get this to work with automated deployments I had to tweak the following on the web heads:

* changed '/etc/apache2/sites-enabled/example.com.conf' to point to capistrano deployment
* precompile assets on machine (not sure why it didnt do this)
* database.yml file was wrong

On the database server: 

* granted all permissions on rails@10.% account. I think we need to come up with a better approach to this.


I ended up using key forwarding to deploy the github repo. In order to do this I used the public key on the webhead as a deploy key and then ran ssh-add with the private key on my local machine. I set capistrano up to port forward. Not sure this is the best approach. 

I think it would be cool if we could automatically generate a database.yml with the right configuration info and not store production db credentials in the projects repo.

There are possible other changes I made that I didn't document here.

