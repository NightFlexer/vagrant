Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64" #l/p: vagrant/vagrant
  #config.vm.hostname = "test"
  config.vm.disk :disk, size: "10GB", primary: true
  config.vm.network "public_network", ip: "192.168.0.129"
  
  config.vm.provider "virtualbox" do |vb|
  vb.gui = true
  vb.memory = "2048"
  end

  
  config.vm.provision "shell", inline: <<-SHELL
  sudo apt-get update
  sudo apt-get install -y curl vim wget htop tmux 
  sudo apt-get install -y nginx && sudo systemctl stop nginx
  sudo apt-get install -y apache2 && sudo systemctl stop apache2

#--- добавление репы и ключа для php5.6 и 7.2 в Debian 9
  sudo apt install -y ca-certificates apt-transport-https
  wget -q https://packages.sury.org/php/apt.gpg -O- | sudo apt-key add -

  echo "deb https://packages.sury.org/php/ stretch main" | sudo tee /etc/apt/sources.list.d/php.list
  sudo apt update
  sudo apt install -y php5.6
  sudo apt install -y php5.6-cli php5.6-common php5.6-curl php5.6-mbstring php5.6-mysqlnd php5.6-xml php-fpm
  
  SHELL
   
end
