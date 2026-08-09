# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Apple Silicon (M1/M2/M3/M4) uyumlu Ubuntu ARM64 box
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.box_version = "202510.26.0"

  # Django/API uygulaması için port yönlendirme
  config.vm.network "forwarded_port", guest: 8000, host: 8000

  config.vm.provision "shell", inline: <<-SHELL
    systemctl disable apt-daily.service
    systemctl disable apt-daily.timer

    sudo apt-get update
    sudo apt-get install -y python3-venv zip

    touch /home/vagrant/.bash_aliases

    if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
      echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
      echo "alias python='python3'" >> /home/vagrant/.bash_aliases
    fi
  SHELL

end