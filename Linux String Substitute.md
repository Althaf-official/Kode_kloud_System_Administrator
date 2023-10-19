### The backup server in the Stratos DC contains several template XML files used by the Nautilus application. However, these template XML files must be populated with valid data before they can be used. One of the daily tasks of a system admin working in the xFusionCorp industries is to apply string and file manipulation commands!



Replace all occurances of the string Text to Maritime on the XML file /root/nautilus.xml located in the backup server.

```
sed -i 's/Text/Maritime/g' /root/nautilus.xml

```



sed: This is the Stream EDitor, a Unix/Linux command-line utility that processes and transforms text using simple, compact programming commands.

`-i`: This is an option for sed that specifies "in-place" editing.
When you use the -i option, sed directly modifies the file specified, which, in this case, is /root/nautilus.xml.


`'s/Text/Maritime/g'`: This is the sed command itself.
It is enclosed in single quotes to prevent the shell from interpreting any special characters within it.
Let's break down the command part by part:

`s`: This is the command used to perform a substitution.

`/Text/Maritime/`: This is the pattern you want to search for and the replacement string.
Here, it's looking for the string "Text" and replacing it with "Maritime."

`g`: This is a flag that stands for "global." When you include g at the end of the sed command,
it ensures that all occurrences of the pattern within each line of the file are replaced. If you omit the g, only the first occurrence on each line is replaced.

`/root/nautilus.xml`: This is the path to the XML file you want to apply the sed command to.
In this case, the file is located at /root/nautilus.xml on the filesystem.

In summary, the sed -i 's/Text/Maritime/g' /root/nautilus.xml command tells sed to perform an in-place substitution within the /root/nautilus.xml file,
replacing all occurrences of "Text" with "Maritime" throughout the file.




``` ruby
thor@jump_host ~$ ssh user@backup_server_ip "sed -i 's/Text/Maritime/g' /root/nautilus.xml"
                                                            
^C
thor@jump_host ~$ ssh clint@stbkp01 "sed -i 's/Text/Maritime/g' /root/nautilus.xml"
The authenticity of host 'stbkp01 (172.16.238.16)' can't be established.
ECDSA key fingerprint is SHA256:MV9XOlfzP43KAmXF4f2SUGAFCPw3TmekN1iAtWM28OE.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stbkp01,172.16.238.16' (ECDSA) to the list of known hosts.
clint@stbkp01's password: 
sed: can't read /root/nautilus.xml: Permission denied
thor@jump_host ~$ sudo s^C
thor@jump_host ~$ 
thor@jump_host ~$ 
thor@jump_host ~$ ssh clint@stbkp01
clint@stbkp01's password: 
[clint@stbkp01 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for clint: 
[root@stbkp01 ~]# sed -i 's/Text/Maritime/g' /root/nautilus.xml
[root@stbkp01 ~]# cat /root/nautilus.xml
<?xml version="1.0"?>   
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   
   <?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>

<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>


<?xml version="1.0"?>
<catalog>
   <book id="bk101">
<author>Menon, Vardaan</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk102">
<author>An, Darshi</author>
      <title>Software Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk103">
<author>Jose Almaraz</author>
      <title>Application Development</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk104">
<author>S, Biswa</author>
      <title>SOA Architecture</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk105">
<author>Mel Jones</author>
      <title>BT</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>
   <book id="bk106">
<author>Solo, Han</author>
      <title>Enterprise Apps</title>
      <genre>Sample</genre>
      <type>Random</type>
      <about>About</about>
      <price>44.95</price>
      <string>String</string>
      <text>Maritime</text>
      <publish_date>2000-10-01</publish_date>
      <description>Unknown Description</description>
   </book>[root@stbkp01 ~]# 

```
