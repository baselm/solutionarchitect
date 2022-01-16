#Install LAMP Stack
sudo yum -y update
sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2

sudo yum install -y httpd mariadb-server
sudo systemctl start httpd

sudo systemctl enable httpd
sudo systemctl is-enabled httpd
# Check config 
service httpd status
service mariadb status
php -v 
#Get the WebSite Code 
#Get the website setup code 
 wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/ILT-TF-200-ACACAD-20-EN/mod4-challenge/setup.tar.gz
tar -zxvf setup.tar.gz
#get the DB files 
wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/ILT-TF-200-ACACAD-20-EN/mod4-challenge/db.tar.gz
tar -zxvf db.tar.gz
#Get the Cafe Website code 
wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/ILT-TF-200-ACACAD-20-EN/mod4-challenge/cafe.tar.gz
tar -zxvf cafe.tar.gz
#Setup the Cafe Parameters frm Systems manager 
1. Create a Cafe Role
3. Assign the role to the cloud9 EC2
2. Set Parameters
./setup/set-app-parameters.sh 
#Configure the MySQL database to support the café application.

./db/set-root-password.sh  
./db/create-db.sh  
#mount the file system 
Assign the Web SG to the Cloud9 EC2
ln -s /var/www/ /home/ec2-user/environment
sudo chown ec2-user:ec2-user /var/www/html
sudo mount -t efs -o tls fs-0b0b5104cb6d1dd5e:/ /var/www/html/
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-0b0b5104cb6d1dd5e.efs.eu-west-1.amazonaws.com:/ /var/www/html/