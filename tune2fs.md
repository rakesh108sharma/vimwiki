[[LINUX]]
# tune2fs

## List/show the configuration
`tune2fs -l /dev/sdXN`


## Set the filesystem label to MY_LABEL:         
`tune2fs -L 'MY_LABEL' /dev/sdXN`


## counts for filesystem check

Set the max number of counts before a filesystem is checked to 20:
`tune2fs -c 20 /dev/sdXN`

Check on next boot:
`tune2fs -c 1 /dev/sdXN`

Never check:
`tune2fs -s -1 /dev/sdXN`

       
               
