# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
# すべてのVagrantの設定は、以下で行います。
# Vagrant.configureの"2"は、コンフィギュレーションバージョンを設定します。
# （古いスタイルを、後方互換性のためにサポートしています）
# あなたがこの事をよく分からない場合、変更しないでください。
# すでに設定が完了しています。
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.
  # 最も一般的な設定オプションについては、以下のコメントによって説明しています。
  # 完全なリファレンスについては、以下のオンラインドキュメントを参照してください。
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  # 全てのVagrant開発環境にはボックスが必要です。
  # ボックスはhttps://atlas.hashicorp.com/search で検索できます。
config.vm.box = "CentOS7.0"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # ボックスの自動アップデート確認を無効にします。
  # これを無効にすると、ユーザーは `vagrant box outdated` を実行したときにのみボックスの更新がチェックされます。
  # これはおすすめしません。
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # ホストマシン上のポートから、マシン内の特定のポートにアクセスするための、転送されたポートマッピングを作成します。
  # 以下の例では、"localhost:8080"にアクセスすると、ゲストマシンの80番ポートにアクセスされます。
  # ※：これにより、開いているポートへのパブリックアクセスが可能になります。
  # config.vm.network "forwarded_port", guest: 80, host: 8080
config.vm.network :forwarded_port, guest: 3000, host: 3000 

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # ホストマシン上のポートから、マシン内の特定のポートにアクセスするための、転送されたポートマッピングを作成し、
  # 公開アクセスを無効にするために、"127.0.0.1"を介したアクセスのみを許可します。
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # プライベートネットワークを作成することで、特定のIPを使用してゲストマシンへの
  # ホストオンリーアクセスが可能になります
config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # ブリッジ接続によるパブリックネットワークを作成します。
  # ブリッジネットワークにより、ゲストマシンはネットワーク上の別の物理デバイスとして表示されます。
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # 追加のフォルダを、ゲストVMに共有します。
  # 最初の引数は、ホスト上の実際のフォルダへのパスです。
  # 2番目の引数は、ゲスト上のフォルダをマウントするパスです。
  # 3番目の引数は、必須でないオプションのセットです。
  # ※nfs: true
  # synced_folderにnfsを使用する。・・・windowsホストでは機能しない。
  # config.vm.synced_folder "../data", "/vagrant_data"
config.vm.synced_folder ".", "/vagrant", nfs: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # プロバイダー固有の設定により、様々なバッキングプロバイダーを、vagrantのために微調整することができます。
  # これはプロバイダ固有のオプションを公開します。
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   # マシン起動時にVirtualBox GUIを表示する。
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   # VM上のメモリ量をカスタマイズする。
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.
  # 使用可能なオプションの詳細については、使用しているプロバイダのドキュメントを参照してください。
config.vm.provider "virtualbox" do |vb|
  #   # "modifyvm", :id
  #   # vb.customizeを使用する時の呪文・・・？
  #
  #   # "--ioapic", "on"
  #   # IO APICをONにする
  #   # ※ http://vboxmania.net/content/%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E8%A8%AD%E5%AE%9A
  #
  vb.customize ["modifyvm", :id, "--ioapic", "on"] 
end

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # Atlasにプッシュ（デプロイ）するための、Vagrantプッシュ方法の定義
  # FTPやHerokuなどの、ほかのプッシュ方法も利用できます。
  # 詳細については、https://docs.vagrantup.com/v2/push/atlas.html のドキュメントを参照してください。
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # シェルスクリプトによるプロビジョニングを有効にします。
  # Puppet, Chef, Ansible, Salt, Dockerなどのプロビジョナも利用できます。
  # 具体的な構文と使用方法の詳細については、ドキュメントを参照してください。
  # ※Vagrantにおけるプロビジョナは、自動的にソフトウェアをインストールしたり、設定を変更したり、そのほかいろいろなことをvagrant upプロセスの一部としてできるようにする。
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
