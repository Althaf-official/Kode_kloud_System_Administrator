# On Nautilus storage server in Stratos DC, there is a storage location named /data, which is used by different developers to keep their data (non confidential data). One of the developers named jim has raised a ticket and asked for a copy of their data present in /data/jim directory on storage server. /home is a FTP location on storage server itself where developers can download their data. Below are the instructions shared by the system admin team to accomplish this task.



a. Make a jim.tar.gz compressed archive of /data/jim directory and move the archive to /home directory on Storage Server.


To create a compressed archive of the /data/jim directory and move it to the /home directory on the Nautilus storage server, you can use the tar command. Here are the steps you can follow:

Log in to the Nautilus storage server using SSH or any other method you have access to.

Open a terminal on the server.

Run the following command to create a jim.tar.gz archive of the /data/jim directory:

```
tar -czvf /home/jim.tar.gz -C /data jim
```
```ruby
tar: The command to create and manipulate tar archives.
-czvf: Options for tar command:
-c: Create a new archive.
-z: Compress the archive using gzip.
-v: Verbose mode (optional but shows progress).
-f: Specifies the archive file to create.
```
Once the jim.tar.gz archive is created, you can move it to the /home directory using the mv command:

```
mv /home/jim.tar.gz /home/

```
Jim can now access the compressed archive from the /home directory and download it to their local machine.

Make sure that Jim has the necessary permissions to read the /data/jim directory and write to the /home directory. 
If needed, you can adjust the permissions using the chmod and chown commands.
