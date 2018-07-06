FROM wordpress:latest

#ENV GITHUB_KEY=${GITHUB_KEY}

RUN apt-get update && \
	apt-get install -y --no-install-recommends ssl-cert && \
	apt-get install sudo && \
	apt-get install -y git-core && \
	#cd /var/www/html/ && \
	#git clone https://34d694e3f70b078418d4613de344d68375f6f678:x-oauth-basic@github.com/s360/WP-Starter.git base2 && \
	rm -rf /var/lib/apt/lists/* && \
	a2enmod ssl
	#a2enmod ssl && \
	#a2ensite default-ssl

# Update aptitude with new repo
#RUN apt-get update

# Install software 
#RUN apt-get install -y git
# Make ssh dir
#RUN mkdir /root/.ssh/

# Copy over private key, and set permissions
#ADD id_rsa /root/.ssh/id_rsa

# Create known_hosts
#RUN touch /root/.ssh/known_hosts
# Add bitbuckets key
#RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts
#RUN ssh-keyscan github.com >> /root/.ssh/known_hosts

# Clone the conf files into the docker container
#RUN git clone git@bitbucket.org:User/repo.git
#RUN git clone https://34d694e3f70b078418d4613de344d68375f6f678:x-oauth-basic@github.com/s360/WP-Starter.git base
#RUN usermod -aG www-data root
RUN mkdir -p /var/www/bintang_theme
#ADD bintang_theme /var/www/html/wp-content/themes/bintang_theme
#ADD sage /var/www/html/wp-content/themes/sage
#RUN chown -R www-data.www-data /var/www/html/wp-content/themes/sage
#RUN mkdir -p /var/www/html/wp-content/themes/bintang_theme
#RUN su -u www-data mkdir -p /var/www/html/wp-content/themes/bintang_theme
#RUN touch /root/www/html/base/tes3.txt
#RUN git clone https://github.com/halilintar8/wp2.git /var/www/html2/
#RUN echo ${GITHUB_KEY}
RUN git clone https://${GITHUB_KEY}:x-oauth-basic@github.com/roots/sage.git /var/www/bintang_theme/sage
RUN git clone https://${GITHUB_KEY}:x-oauth-basic@github.com/s360/WP-Starter.git /var/www/bintang_theme/starter
RUN git clone https://${GITHUB_KEY}:x-oauth-basic@github.com/s360/contender.git /var/www/bintang_theme/theme

#RUN chown -R root.root /var/www/
#RUN chown -R www-data.www-data /var/www/bintang_theme/
RUN cp -r /var/www/bintang_theme/starter/Themes/* /var/www/bintang_theme/sage/
RUN cp -r /var/www/bintang_theme/theme/* /var/www/bintang_theme/sage/
RUN chown -R www-data.www-data /var/www/bintang_theme/
#RUN sudo -u www-data touch /var/www/html/tes3.txt
#WORKDIR /var/www/html
#RUN touch /var/www/html/tes2.txt
#USER www-data
RUN mkdir -p /var/www/html/tes5
#RUN sudo -u www-data mkdir -p /var/www/html/tes5
#RUN sudo -u www-data cp -r /var/www/bintang_theme/sage/* /var/www/html/wp-content/themes/sage/
#COPY /var/www/bintang_theme/sage /var/www/html/wp-content/themes/

#RUN apt-get install git-core
#ADD ~/.ssh/known_hosts
#RUN ssh-keyscan github.com >> ~/.ssh/known_hosts
#RUN cd /var/www/html/
#RUN git clone https://34d694e3f70b078418d4613de344d68375f6f678:x-oauth-basic@github.com/s360/WP-Starter.git base2

# Add composer
RUN curl -sS https://getcomposer.org/installer | php && \
mv composer.phar /usr/local/bin/composer && \
composer self-update
#composer self-update && \

# Add WP-CLI 
RUN curl -o /bin/wp-cli.phar https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
COPY wp-su.sh /bin/wp
RUN chmod +x /bin/wp-cli.phar /bin/wp

EXPOSE 80
EXPOSE 443

