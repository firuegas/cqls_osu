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


### Scheduler 
SGE infrastructure of the CQLS-OSU cluster, 
```bash
SGE_Batch -c “./tu script” -P 1 -q bpp -r jobname
```
>Basic Usage:
  `SGE_Batch -c '<command>' -m <max_memory> -f <free_mem_request> -F <max_file_size> -P <number_processors> -r <Run_ID> -p <priority> -M <email_address> -q <queue> -Q`
 -c	The command to submit. (REQUIRED: Make sure to use '')\
 -t	Array Job Range to submit (e.g. 1-100).\
 -b	Array Job Maximum Task Concurrency ('batch size'; default 50).\
 -F	Kill the job if any created file exceeds this size (100M, 1G, 4G, 32G etc.).\
 -f	Free memory to request on the machine to run this job (100M, 1G, 4G, 32G etc.).\
 -m	Maximum memory this job may use (kill if exceeded) (100M, 1G, 4G, 32G etc.).\
 -P	The number of processors needed for this job if you have a threaded application (default 1).\
 -r	The SGE RunID and Log Output Directory Name. (REQUIRED)\
 -q	The QUEUE to use. (default to use any node you have access to)\
 -Q	Don't print any output to the screen. (Use then when you are running many jobs at once).\
 -p	The priority of job submitted. (range -10 to 10, default 0)\
 -M	Email address to send notification at beginning and end of job.\
 -S	Shell option: Setting this option will change the default shell from "bash" to "tcsh". (defualt "bash").\
 -h	Print Help Page.

   
# Metapipeline

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

