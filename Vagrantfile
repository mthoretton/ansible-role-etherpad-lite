$prepare = <<SCRIPT
sudo apt-get update
# hack for vagrant+windows compatibility
for i in `find /vagrant -type f \( -name "hosts" \)`; do    sed -i 's/\r//' $i && chmod +x $i ; done
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.network "forwarded_port", guest: 9001, host: 9001

  config.vm.provision "shell", inline: $prepare
  config.vm.provision "shell",
    :path => "tests/specs.sh",
    :upload_path => "/home/vagrant/specs",
    # change role name below
    :args => "--install ansible-role-etherpad-lite"

  # Forward des connexions ssh
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |v|
    v.name   = "ansible-role-etherpad-lite"
    v.memory = 2048
  end
end
