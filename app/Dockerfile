FROM ruby:2.4.1
ARG name=nepaldecide
ENV APP_NAME=${name}

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
ADD ./development_app /decidim/development_app
WORKDIR /decidim
RUN bundle install
RUN yarn install

WORKDIR /decidim/development_app
CMD [ "bundle", "exec", "rails", "s" ]