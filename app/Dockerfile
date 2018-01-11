FROM ruby:2.4.1
ENV APP_NAME=development_app
ENV APP_HOME /decidim/${APP_NAME}
ENV domain=localhost
RUN mkdir -p /usr/local/etc \
  && { \
    echo 'install: --no-document'; \
    echo 'update: --no-document'; \
  } >> /usr/local/etc/gemrc


# Node.js
RUN curl -sL https://deb.nodesource.com/setup_9.x | bash - \
    && apt-get install -y nodejs

# yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -\
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
    && apt-get update \
    && apt-get install -y yarn git

RUN git clone https://github.com/decidim/decidim.git /decidim
ADD ./development_app ${APP_HOME}
WORKDIR ${APP_HOME}
RUN bundle install
RUN yarn install
RUN mkdir $APP_HOME/.ssh \
  && mkdir $APP_HOME/tmp/pids \
  && cd $APP_HOME/.ssh \
  && pwd \
  && openssl genrsa -des3 -passout pass:dummypassword -out $domain.key 2048 -noout \
	&& openssl rsa -in $domain.key -passin pass:dummypassword -out $domain.key \
	&& openssl req -new -key $domain.key -out $domain.csr -passin pass:dummypassword \
    -subj "/C=US/ST=VA/L=Falls Church/O=IT/OU=IT/CN=$domain/emailAddress=techsupport@ctacdev.com" \
  && openssl x509 -req -days 365 -in $domain.csr -signkey $domain.key -out $domain.crt

EXPOSE 3000

WORKDIR ${APP_HOME}
CMD [ "bundle", "exec", "puma", "-C", "config/puma.rb" ]