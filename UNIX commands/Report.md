## Objective
To document and understand the basic **UNIX shell commands** used throughout Cadence Virtuoso and HSPICE-based VLSI design workflows.  
These commands are essential for file management, directory navigation, simulation setup, and tool execution in a Linux-based environment.

---

## Commonly Used UNIX Commands

| **Command** | **Example** | **Description** |
|:-------------|:------------|:----------------|
| `ls` | `ls -alF` | Lists files and directories in the current working directory. |
| `cd` | `cd Lab3_InverterLayout_StickDiagram` | Changes the current directory. |
| `pwd` | `pwd` | Displays the full path of the current directory. |
| `mkdir` | `mkdir layouts` | Creates a new directory. |
| `rmdir` | `rmdir temp` | Removes an empty directory. |
| `cp` | `cp file1.sp backup.sp` | Copies a file or directory. |
| `mv` | `mv old.sp new.sp` | Moves or renames a file. |
| `rm` | `rm -rf *.log` | Deletes files or directories (use with caution). |
| `more` | `more result.mt0` | Displays the content of a file one page at a time. |
| `nedit` | `nedit run_tb_inv.sp` | Opens the NEdit text editor to modify SPICE or netlist files. |
| `cat` | `cat file1 file2 > combined.txt` | Concatenates files or displays contents. |
| `man` | `man ls` | Displays the manual page for a given command. |
| `lpr` | `lpr report.txt` | Sends a file to the printer. |
| `^C` | *(Ctrl + C)* | Terminates a running process. |
| `^Z` | *(Ctrl + Z)* | Suspends a running process. |
| `bg` | `bg` | Resumes a suspended job in the background. |
| `fg` | `fg` | Brings a background job to the foreground. |
| `yppasswd` | `yppasswd` | Changes user password in a UNIX network environment. |

---

## Usage in VLSI Design Workflow
These commands were used during lab sessions to:

- **Create and organize** project directories (`mkdir`, `cd`, `ls`).  
- **Edit and manage** HSPICE simulation files (`nedit`, `cat`, `mv`, `cp`).  
- **Run and control** background processes for Cadence tools (`bg`, `fg`, `^C`, `^Z`).  
- **Inspect and verify** extracted netlists, log files, and simulation results (`more`, `ls -al`, `pwd`).  

---

## Example Workflow
```bash
# Navigate to simulation folder
cd ~/Cadence/Lab3_InverterLayout_StickDiagram

# View files
ls -al

# Edit HSPICE testbench file
nedit run_tb_inv.sp &

# Run simulation
hspice run_tb_inv.sp > result.log &

# View results
more result.mt0
