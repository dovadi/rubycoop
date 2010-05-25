desc "deploy site to rubycoop"
task :deploy do
  require 'rubygems'
  require 'highline/import'
  require 'net/ssh'

  branch = "master"

  Net::SSH.start('dovadi.com', 'dovadi') do |ssh|
    commands = <<EOF
cd ~/rubycoop
git checkout #{branch}
git pull origin #{branch}
git checkout -f
rm -rf _site
jekyll --no-auto
EOF
    commands = commands.gsub(/\n/, "; ")
    ssh.exec commands
  end
end
