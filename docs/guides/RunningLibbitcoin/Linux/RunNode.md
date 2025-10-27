# Run Libbitcoin Node

To run the node, execute `bn` and the node will start.

If built according to the _Build From Source_ guide, the executable can be found in the `home/user/libbitcoin-node/prefix/bin` directory.

### Command line help

<details>
<summary>There are several command line options, which can be displayed by adding `-h`:</summary>
<br>

```
./bn -h
```
<br>


```
Usage: bn [-abdfhiklnrstvw] [--config value]                             
Info: Runs a full bitcoin node.                                          
Options (named):
-a [--slabs]         Scan and display store slab measures.               
-b [--backup]        Backup to a snapshot (can also do live).            
-c [--config]        Specify path to a configuration settings file.      
-d [--hardware]      Display hardware compatibility.                     
-f [--flags]         Scan and display all flag transitions.              
-h [--help]          Display command line options.                       
-i [--information]   Scan and display store information.                 
-k [--buckets]       Scan and display all bucket densities.              
-l [--collisions]    Scan and display hashmap collision stats (may exceed
                     RAM and result in SIGKILL).                         
-n [--newstore]      Create new store in configured directory.           
-r [--restore]       Restore from most recent snapshot.                  
-s [--settings]      Display all configuration settings.                 
-t [--test]          Run built-in read test and display.                 
-v [--version]       Display version information.                        
-w [--write]         Run built-in write test and display.
```
<br>

</details>

### Milestone sync

By default, it will do a milestonesync. Meaning that it will not do a full consensus validation (including all script checks) before the milestone (by default block 900000).
This can be changed using the config file.
