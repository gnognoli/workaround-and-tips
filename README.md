# How to install latest ruby with latest ssl lib  on ubuntu using rbenv
How to install
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc

RUBY_CONFIGURE_OPTS=--with-openssl-dir=/usr/lib/ssl rbenv install 3.1.2
