#install puppet
apt-get install puppet
puppet module install puppetlabs-apt
puppet module install puppet-nodejs
puppet module install puppetlabs-apache

#cat 1.pp
class { 'apache': }
class { 'nodejs': }

puppet apply 1.pp


#install yarn 

curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn

#build

git clone https://github.com/fullmooninu/thelounge.git
cd thelounge
yarn install
NODE_ENV=production yarn build
yarn start
