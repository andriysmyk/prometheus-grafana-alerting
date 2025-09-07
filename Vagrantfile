Vagrant.configure("2") do |config|
  # VM1 - Target with load
  config.vm.define "target" do |target|
    target.vm.box = "ubuntu/focal64"
    target.vm.hostname = "target"
    target.vm.network "private_network", ip: "xxx.xxx.xxx.xxx"
    target.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end
  end

  # VM2 - Monitoring (Prometheus, Grafana, Alertmanager)
  config.vm.define "monitoring" do |monitoring|
    monitoring.vm.box = "ubuntu/focal64"
    monitoring.vm.hostname = "monitoring"
    monitoring.vm.network "private_network", ip: "xxx.xxx.xxx.xxx"
    monitoring.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    # Forward ports for easy access from host
    monitoring.vm.network "forwarded_port", guest: 3000, host: 3000   # Grafana
    monitoring.vm.network "forwarded_port", guest: 9090, host: 9090   # Prometheus
    monitoring.vm.network "forwarded_port", guest: 9093, host: 9093   # Alertmanager
  end
end
