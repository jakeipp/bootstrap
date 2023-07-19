FROM ruby

WORKDIR /app
COPY . /app/

RUN tar -xzf freetds-1.1.24.tar.gz
WORKDIR freetds-1.1.24
RUN ./configure --prefix=/usr/local --with-tdsver=7.3
RUN make
RUN make install

WORKDIR /app
ENV BUNDLE_PATH /gems
RUN bundle install

COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

EXPOSE 3000
CMD ["bin/rails", "server", "-b", "0.0.0.0"]
