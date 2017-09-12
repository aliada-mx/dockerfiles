# build: 
#   docker build -t babasbot/codeship-gcloud-ruby:2.4.1 .
# run:
#   docker run --rm -it babasbot/codeship-global-ruby:2.4.1 sh
FROM codeship/google-cloud-deployment

RUN \
  apt-get update && apt-get install -y \
    build-essential \
    curl \
    git \
    zlib1g-dev \
    libssl-dev \
    libreadline-dev \
    libyaml-dev \
    libxml2-dev \
    libxslt-dev

RUN apt-get clean

RUN git clone https://github.com/sstephenson/rbenv.git /root/.rbenv
RUN git clone https://github.com/sstephenson/ruby-build.git /root/.rbenv/plugins/ruby-build
RUN /root/.rbenv/plugins/ruby-build/install.sh

ENV PATH /root/.rbenv/bin:$PATH

RUN eval "$(rbenv init -)"

RUN rbenv install 2.4.1
RUN rbenv global 2.4.1

RUN echo 'eval "$(rbenv init -)"' >> ~/.bashrc
RUN echo 'eval "$(rbenv init -)"' >> ~/.profile

ENV CONFIGURE_OPTS --disable-install-doc
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc
