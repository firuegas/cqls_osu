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
SGE infrastructure of the CQLS-OSU cluster 
_SGE submission examples_
```bash
# general submission work
SGE_Batch -c “./tu script” -P 1 -q bpp -r jobname
# specific hots submission work
SGE_Batch -c “./tu script” -P 1 -q bpp@cerebro -r jobname
```
_Development session_
```bash
# running development session in a specific host
qrsh -q bpp@cerebro
```
Note: you can use the commands below to specify memory, processors, etc.

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

### CQLS available host
```
SGE_Avail
#                 HOST TOTRAM FREERAM    TOTSLOTS                 Q  QSLOTS  QFREESLOTS   QSTATUS     QTYPE
#                 amp  1007.6   977.5         128               bpp     107         107    normal       BIP
#             cerebro  1007.3   986.6         256               bpp     171         103    normal       BIP
#              anduin  1007.6   977.5         128               bpp      86          86    normal       BIP
#              selway  1007.6   964.1         128               bpp      86          86    normal       BIP
#           symbiosis  1007.4   991.7         128               bpp      89          67    normal       BIP
#              debary  1007.6   936.9         128               bpp      86          50    normal       BIP
#               galls   503.7   477.0          64               bpp      44          24    normal       BIP
#               cedro   503.7   492.1          64               bpp      44          18    normal       BIP
``` 

-------
## Metapipeline

> Raw pipeline for PacBio genome assemblies of _P. ramorum_
```R
"Assembly reads" 
   Nextdenovo -> Pacbio # reads assembly
   "QStats "
      assembly -> Braker # contig annotation
      "Genome annotated"
         <Comparative genomics> -> What Tools?
```

# Suggested and notes 
```sh
hgap-4 -> Falcon-unzip -> purge_haplotigs -> SSPACE_LongRead
```

#for nano pore assemblies 
```bash
flye # to aassembly de novo 
```

-------
## Setting $PATH and env
in `.bashrc` add 

```bash
export PATH=$PATH:/.local/to_folder
```
and 
in the `.tcshrc`, set the enviroment by adding
```bash
set PATH $HOME/.local/to_folder/:$PATH
```

----------------------
### CGRB/CQLS useful links
[UNIX hpc cluster basic information](https://cosine.oregonstate.edu/faqs/unix-hpc-cluster)
[CGRB infrastructure](https://shell.cqls.oregonstate.edu/files/cgrb_infrastructure.pdf)
