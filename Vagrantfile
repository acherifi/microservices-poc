## .1 IP addresses are used by the router -> starting IPs at 2
Vagrant.configure("2") do |config|
  config.vm.define "gateway" do |gateway|
    gateway.vm.box = "debian/stretch64"
    gateway.vm.network "forwarded_port", guest: 80, host: 80
    gateway.vm.network "forwarded_port", guest: 8080, host: 8080
    gateway.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/gateway/gateway.yaml"
      #ansible.raw_arguments = ["-vvv"]
    end
  end
  config.vm.define "authentication" do |authentication|
    authentication.vm.box = "debian/stretch64"
    authentication.vm.network "private_network", ip: "10.0.1.2"
  end
  config.vm.define "web" do |web|
    web.vm.box = "debian/stretch64"
    web.vm.network "private_network", ip: "10.0.1.3"
  end
  config.vm.define "upload" do |upload|
    upload.vm.box = "debian/stretch64"
    upload.vm.network "private_network", ip: "10.0.1.4"
  end
end