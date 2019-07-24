FROM debian:stretch-slim
#FROM mojibakeumd/docker-rspec-puppet@sha256:3b949ce4cbc17ed86307a1dba229b07ca510f08f71449dc6bb3650c137acb8b3
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
	&& apt-get install software-properties-common -y --force-yes --no-install-recommends \
	&& add-apt-repository 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' \
	&& apt-get update \
	&& apt-get install rubygems ruby-dev wget git make build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev sudo openssh-client python-dev python-pip python-yaml ansible=2.8.2-1ppa~trusty -y --allow-unauthenticated --force-yes --no-install-recommends \
	&& pip install pyrx awscli ansible-lint \
    && gem install librarian-puppet puppet:5.5.14 puppetlabs_spec_helper:0.10.3 puppet-lint:2.3.6 facter:2.5.1 rspec_junit_formatter:0.2.3 parallel_tests:2.7.0 toml-rb bundler \
    && wget https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz \
    && tar xzf Python-3.7.3.tgz \
    && cd Python-3.7.3 \
    && ./configure --enable-optimizations \
    && make altinstall \
    && cd .. \
    && rm -rf Python-3.7.3* /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && sed -i 's/httpredir.debian.org/aptrepo.piksel.com/g' /etc/apt/sources.list \
    && apt-get clean \