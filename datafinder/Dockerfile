FROM drupal:php8.3-apache-bullseye

# Data finder steps
RUN apt-get update && apt-get install git unzip -y && \
    	git clone https://github.com/nyuhpc/CD-finder.git && \
    	composer require 'drupal/paragraphs:^1.17'&& \
	composer require 'drupal/backup_migrate:^5.0' && \
	composer require 'drush/drush'

RUN drush si --yes \
	standard \
	--db-url=sqlite://sites/finder/files/.ht.sqlite \
	--site-name=data-finder

COPY .ht.sqlite /opt/drupal/web/sites/finder/files/.ht.sqlite

RUN chown -R www-data:www-data web/sites web/modules web/themes; 	
