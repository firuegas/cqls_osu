# Computational Quantitative Life Science cluster at Oregon State University
## CQLS@OSU
### Setup and setting of the Computational Quantitative Life Science cluster

   You've been given an account on the following machine:

               shell.cgrb.oregonstate.edu

               Command Line Access:
               ssh -p 732 username@shell.cgrb.oregonstate.edu

               Please use the following machine to upload and download data:
               Server:

               	files.cgrb.oregonstate.edu

               SFTP Access:
               	sftp -o Port=732 username@files.cgrb.oregonstate.edu
               	scp -P 732 <files to upload> username@files.cgrb.oregonstate.edu:
               
               Samba/SMB Access:
               	Windows: \\files.cgrb.oregonstate.edu
               	Mac: smb://files.cgrb.oregonstate.edu
                  
                  
                  
> Notes:
> All programs are in `/local/cluster/`
> Aparently, you have to call each program from its PATH, so double check that carefully.
> Also, the nodes are specified independently, so double check that you are running optimally.

> Raw pipeline for PacBio genome assemblies of P. ramorum
```bash
-> hgap-4 -> Falcon-unzip -> purge_haplotigs -> SSPACE_LongRead
```
#for nano pore assemblies 
```bash
flye # to aassembly de novo 
```


# setting $PATH and env

in `.bashrc` add 

```bash
export PATH=$PATH:/.local/to_folder
```
   
and in the `.tcshrc`, set the enviroment by adding
```bash
set PATH $HOME/.local/to_folder/:$PATH
```

