FROM drupal:php8.3-apache-bullseye

# Data finder steps
RUN apt-get update && apt-get install git rsync -y && \
    git clone https://github.com/nyuhpc/CD-finder.git /opt/drupal/web/modules/cd-finder && \
    composer require 'drupal/paragraphs:^1.17'&& \
	composer require 'drush/drush'

RUN drush si --yes \
	standard \
	--db-url=sqlite://sites/default/files/.ht.sqlite \
	--site-name=data-finder

RUN drush en finder --yes

COPY .ht.sqlite 	/opt/drupal/web/sites/default/files/.ht.sqlite
COPY .ht.sqlite-wal	/opt/drupal/web/sites/default/files/.ht.sqlite-wal
COPY .ht.sqlite-shm	/opt/drupal/web/sites/default/files/.ht.sqlite-shm

RUN chown -R www-data:www-data web/sites web/modules web/themes; 	
