ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro' 

# Описываем Виртуальные машины
MACHINES = {
# Указываем имя ВМ "name"
  :"ansible" => {
              #Какой vm box будем использовать
              :box_name => "ubuntu/22.04",
              #Указываем количество ядер ВМ
              :cpus => 2,
              #Указываем количество ОЗУ в мегабайтах
              :memory => 2048,
              :ip_addr => '192.168.74.12'
            },
  :"webnginx" => {
              #Какой vm box будем использовать
              :box_name => "ubuntu/22.04",
              #Указываем количество ядер ВМ
              :cpus => 2,
              #Указываем количество ОЗУ в мегабайтах
              :memory => 2048,
  	      :ip_addr => '192.168.74.13'
            },
}
Vagrant.configure("2") do |config|
  MACHINES.each do |boxname, boxconfig|
    # Отключаем проброс общей папки в ВМ
    config.vm.synced_folder ".", "/vagrant", disabled: true
    # Применяем конфигурацию ВМ
    config.vm.define boxname do |box|
      box.vm.box = boxconfig[:box_name]
      box.vm.host_name = boxname.to_s
      box.vm.provider "virtualbox" do |v|
        v.memory = boxconfig[:memory]
        v.cpus = boxconfig[:cpus]
        box.vm.network("private_network", ip: boxconfig[:ip_addr])
      end
    end
  end
end
