FROM mojibakeumd/docker-rspec-puppet@sha256:3b949ce4cbc17ed86307a1dba229b07ca510f08f71449dc6bb3650c137acb8b3

RUN apt-get update \
	&& apt-get install software-properties-common -y \
	&& add-apt-repository 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' \
	&& apt-get update \
	&& apt-get install sudo openssh-client python-dev python-pip python-yaml ansible=2.7.2-1ppa~trusty -y \
	&& rm -rf /var/lib/apt/lists/* \
	&& sed -i 's/httpredir.debian.org/aptrepo.piksel.com/g' /etc/apt/sources.list

RUN pip install -U pip \
	&& pip install pyrx awscli ansible-lint

RUN gem install librarian-puppet puppet:5.5.14 puppetlabs_spec_helper:0.10.3 puppet-lint:2.3.6 facter:2.5.1 rspec_junit_formatter:0.2.3 parallel_tests:2.7.0 toml-rb

RUN wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz \
    && tar xzf Python-3.7.3.tgz \
    && cd Python-3.7.3 \
    && ./configure --enable-optimizations \
    && make altinstall