include "hadoop"

group { "puppet":
  ensure => "present",
}

exec { 'apt-get update':
 command => '/usr/bin/apt-get update',
}

package { "openjdk-6-jdk" :
 ensure => "present",
 require => Exec['apt-get update']
}

file {
  "/root/.ssh/id_rsa":
  source => "puppet:///modules/hadoop/id_rsa",
  mode => 600,
  owner => root,
  group => root,
  require => Exec['apt-get update']
 }
 
file {
  "/root/.ssh/id_rsa.pub":
  source => "puppet:///modules/hadoop/id_rsa.pub",
  mode => 644,
  owner => root,
  group => root,
  require => Exec['apt-get update']
 }

ssh_authorized_key { "ssh_key":
    ensure => "present",
    key    => "AAAAB3NzaC1yc2EAAAADAQABAAABAQC3ntqwB6V6hl8ieUI0apcfVEPBQr5TOvthGDwYitgx8qjms96OgtVl3FssZ+YIlm8YbiUQ+CWFe5rijdrY7h42atzPcRz5/IH+RjOrXK9jd8K8wPTMQZUi8t6qKTzm8FwIkdWdz5nP9cjuSYYJwwwoeQw9fLY/Vm3jM0oXKPXI9keG0xd6O58S63Y/17tT6kDgKyZq0IvDO2q3I2ctFKfB3PnQKnVsay9ywUAhgbFuJy8HFq1pcENfY7hsnpHUrJR3YzJ7ac7gnSRJecpd2aPBVJlHj1SLhG8iWPBe6jRmwcBOQnsIPT1zWgPp/47N5l8xYAhsBOPYbSJ3Ko4vg953",
    type   => "ssh-rsa",
    user   => "root",
    require => File['/root/.ssh/id_rsa.pub']
}
