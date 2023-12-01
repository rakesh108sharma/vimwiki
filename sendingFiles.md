[[LINUX]]  

# sending files to another PC  

## scp  
good for quick transfer of one file.  
`scp FILE USER@USER-IP:DEST`  
ex: `scp notes.txt rakesh@192.168.1.13:downloads/`  

## sftp  
if you need to transfer more files in both direction, create a "session".
**filezilla** can be used instead.  

## rsync  
Superior way for transfering and synchronizing many files. 

## sshfs  
Great for quickly setting up a link to a remote file system.  
`sshfs USER@USER-IP:/path/to/source MOUNT-FOLDER`  
ex:
`mkdir remote` on DEST PC  
`sshfs rakesh@192.168.1.13;/home/rakesh/public remote`  

The directory can later be unmounted with `umount`  
**BUT**
it is preferable to use `fusermount` for unmounting directories:
`fusermount -u remote`  

## nfs  


## samba  
