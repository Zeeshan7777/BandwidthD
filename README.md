# BandwidthD

#### INSTALLATION #

You must download and install Winpcap or Npcap from: 

https://www.winpcap.org/ or
https://nmap.org/npcap/

I recommend version 4.1.3 Winpcap or version 1.60 Npcap and for Windows 2008 R2 Ncapcap-0.996 at this time.

Then, unzip Bandwidthd to the folder of your choice. Edit 
etc/bandwidthd.conf to suit your environment. Double click 
"Install Service" to install the service.  You can now start 
Bandwidthd from the services control panel.  Stopping the 
service from the services panel not supported.  You will 
need to kill it with task manager if you want it stopped.

If you have more than one network interface card, and you 
want to listen on a specific device, you can run 
"List Device Names" to produce a list of devices that can 
be used on the "dev" line in bandwidthd.conf.  By default, 
Bandwidthd listens on the first interface it detects.

For using 64-bit variant of Bandwidthd with Npcap you need to place both wpcap.dll 
and packet.dll files in Bandwidthd folder you can copy these files from System32\NPcap 
folder and make sure Npcap service is running by typing sc query Npcap on command prompt, 
which show you status either running or stopped otherwise it will use Winpcap API as compatibility 
if you also selected to install Winpcap compatibility mode and for using 32-bit variant with Npcap on 
64 bit OS/platform you need to extract both .dll files 32-bit variant from Npcap setup using 7zip extractor
and place within Bandwidthd folder but need same version also installed on your system.

Both 64 and 32 binaries compiled with the Postgresql database support you can configure 
database options on these Windows version of Bandwidthd and populate database as you like
for Bandwidthd database you need to create tables and indexes from the schema.Postgresql
which provided with binary, but first you need to install Postgresql version which support
your OS and then create database mydb as an example then copy the schema.Postgresql file 
where Postgresql binary reside and then run the command from the Postgresql binary path with
username and database "psql mydb username schema.postgresql". Where mydb is our database
that we created and username is the user from which we created the database by default, 
there is only one username and database which is "postgres".
So after that it will create tables and indexes. You also need to 
configure bandwidth.Conf file to use Postgresql as data collectors. 
Once you have done all things perfectly after some time data populate 
in Postgresql and you can see it with the pgAdmin utility of Postgresql.

Now the last thing you need to see the HTML version of data collecting by Postgresql for that 
you need a Map server for Windows ms4w which already included Postgresql support download and 
extract ms4w where you like. In the Apache folder of ms4w there is another folder htdocs you 
only need to copy all phphtdocs content excluding bd_pgsql_purge.Sh which is postgressql purge
script and place in htdocs folder and make some configuration change in the config.Conf so it 
can connect to the database and retrieves  entries and make graphs on demand, but there is one problem when
retriving entries and plotting graphs it will show you UTC time instead of your local time for 
that you need to edit graph.php file then add this line before mktime(); 
 date_default_timezone_set ('UTC'); and replace your Timezone with 'UTC' if you don't live in the UK like this 'Asia/Karachi'
for more details how to configure these options and bandwidth.Conf file just read README.txt file DATABASE SUPPORT section. 
