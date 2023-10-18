# How to install latest ruby with latest ssl lib  on ubuntu using rbenv

#1 git clone https://github.com/rbenv/rbenv.git ~/.rbenv

#2 echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc

#3 RUBY_CONFIGURE_OPTS=--with-openssl-dir=/usr/lib/ssl rbenv install 3.1.2

#4 rbenv global 3.1.2

#5 exit from your current shell session and reconnect, you should be able to use  the ruby version you newly installed
