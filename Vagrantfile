# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1280
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/getreqs.yml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/prep.yml"
    #ansible.extra_vars = {
    #  mariadb_bind_address: "0.0.0.0",
    #  glance_dockerized_deployment: true
    #}
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/deploy.yml"
    #ansible.extra_vars = {
    #  glance_dockerized_deployment: true,
    #  openstack_mysql_host: "{{ ansible_docker0.ipv4.address }}"
    #}
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/test.yml"
  end

end
