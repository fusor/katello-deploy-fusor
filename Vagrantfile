module RHCI

  Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

    NAME        = 'rhci'
    PARENT_NAME = 'centos6-devel'
    BOX         = KatelloDeploy::BOXES.find { |b| b.fetch(:name) == PARENT_NAME }.merge(:name => NAME)

    KatelloDeploy.define_katello_machine config, BOX

    config.vm.define NAME do |machine|
      machine.vm.provision :shell do |shell|
        # sample RHCI setup
        shell.inline = 'echo doing RHCI setup'
        config.vm.synced_folder '../rhci', '/home/vagrant/rhci'
      end
    end

    config.vm.provider :virtualbox do |domain|
      domain.memory = 1536
    end
  end
end

