# How to install latest ruby with latest ssl lib  on ubuntu using rbenv

#1 git clone https://github.com/rbenv/rbenv.git ~/.rbenv

#2 echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc

#3 RUBY_CONFIGURE_OPTS=--with-openssl-dir=/usr/lib/ssl rbenv install 3.1.2
