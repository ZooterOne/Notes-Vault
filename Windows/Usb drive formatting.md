```
diskpart
```
run the disk partitioning utility.
```
list disk
select disk <num>
```
select the drive to format.
```
clean
create partition primary
select partition 1
format fs=<file system> quick
active
```
rebuild partition and format the drive.
_file system: ntfs | fat32_
```
exit
```
exit the disk partitioning utility.