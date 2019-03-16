# -*- mode: ruby -*-
# vi: set ft=ruby :

machines = {
	"repo" => {"memory"=>"1024", "cpus"=>"2", "ip" => "10" },
	"pipeline" => {"memory"=>"1024", "cpus"=>"2", "ip" => "10" },
	"dev" => {"memory"=>"1024", "cpus"=>"2", "ip" => "10" },
	"homolog" => {"memory"=>"1024", "cpus"=>"2", "ip" => "10" },
	"production" => {"memory"=>"1024", "cpus"=>"2", "ip" => "10" },
}

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  
  machines.each do |name,conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.network "private_network", ip: "192.168.88.#{conf["ip"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.cpus = "#{conf["cpus"]}"
	vb.memory = "#{conf["memory"]}"
	vb.name = "#{name}"
	vb.hostname = "#{name}.dexter.com.br"
      end
      
      if File.file?("provision/#{name}.sh")
	      config.vm.provision "shell", path: "provision/#{name}.sh"
      end 

    end
  end
  config.vm.provision "shell", inline: <<-SHELL
    yum install -y epel-release vim
  SHELL
end
