FROM mojibakeumd/docker-rspec-puppet@sha256:3b949ce4cbc17ed86307a1dba229b07ca510f08f71449dc6bb3650c137acb8b3

RUN apt-get update

RUN apt-get install software-properties-common -y
RUN add-apt-repository 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main'

RUN apt-get update

RUN apt-get install sudo openssh-client python-dev python-pip python-yaml ansible=2.7.2-1ppa~trusty -y

RUN pip install pyrx
RUN pip install awscli
RUN pip install ansible-lint

RUN sed -i 's/httpredir.debian.org/aptrepo.piksel.com/g' /etc/apt/sources.list

RUN gem install librarian-puppet
RUN gem install puppet -v '< 5.0.0'
RUN gem install puppetlabs_spec_helper -v '0.10.3'
RUN gem install puppet-lint -v '>= 1.0.0'
RUN gem install facter -v '>= 1.7.0'
RUN gem install rspec_junit_formatter -v '0.2.3'
RUN gem install parallel_tests
