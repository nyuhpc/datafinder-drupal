FROM drupal:php8.3-apache-bullseye

# Data finder steps
RUN apt-get update && apt-get install git unzip -y && \
    	git clone https://github.com/xtrasimplicity/CD-finder.git /opt/drupal/web/modules/cd-finder && \
    	composer require 'drupal/paragraphs:^1.17'&& \
	composer require 'drush/drush'

RUN drush si --yes \
	standard \
	--db-url=sqlite://sites/finder/files/.ht.sqlite \
	--site-name=data-finder && \
	chown -R www-data:www-data web/sites web/modules web/themes; 	

COPY .ht.sqlite /opt/drupal/web/sites/finder/files/.ht.sqlite


