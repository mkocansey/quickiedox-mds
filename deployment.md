# Deploying Your Documentation


This step is completely optional since developers deploy their websites differently. 

Included with QuickieDox is a deployment script (`deploy-example.php`{.inline}) that has some sample configuration data in there. The script works with the [deployer composer package](https://deployer.org). To use this you will need to run

{.command-line}
```bash
composer require --dev deployer/deployer
```

Next you will need to rename the file from `deploy-example.php`{.inline} to `deploy.php`{.inline}.

You will need to edit the file to match your server details.

{data-line="2,3,6".line-numbers}
```php
host('staging')
	# your domain name or server IP
    ->set('hostname', 'test.quickiedox.com')
    
	# which user on your server will you be deploying as
    ->set('remote_user', 'deployment-user') 
    
    ->set('labels', [ 'stage'=> 'staging'])
    
    # which branch in your repo are you deploying from
    ->set('branch', 'development')
    
    # path to the directory where code should be deployed
    # ideally this is the directory you will serve the doc website from
    ->set('deploy_path', '/var/www/html/test-quickiedox');
```


You will notice there are two host blocks in the `deploy.php`{.inline} file. One for staging and another for production.

To deploy to your staging server you will need to run the following in your command line while at the root of the project.

{.command-line}
```bash
vendor/bin/dep deploy staging
```

To deploy to your production server you will need to run the following in your command line while at the root of the project.

{.command-line}
```bash
vendor/bin/dep deploy production
```