# How to acess aguia4 cluster

## Login and Acess:
```markdown
- SSH: ssh USP_ID@shark.hpc.usp.br
- Password: USP_ID password
- shark ssh aguia4

```
## Utilities

```markdown
- sbatch namejob.sh            : Puts `namejob.sh` in the queue
- scancel job_id               : Cancels the job
- squeue --user=nnnn           : Displays the jobs of user `nnnn`
- scontrol show jobid <jobid>  : Shows information about the job with identification `<jobid>`
- module avail                 : Lists the installed programs
```

For more: [slurm workload manager](https://slurm.schedmd.com/pdfs/summary.pdf)

**Pay attention!**: Don't use your directory for permanent data storage. After transferring your files, remove them from your directory.

---

## Job Template 

To allow Slurm to allocate more than one job on the same server, use the following job template.

```markdown
#!/bin/bash 

#SBATCH --partition=SP2
#SBATCH --ntasks=1            : Number of tasks / MPI processes
#SBATCH --cpus-per-task=1      : Number of threads OpenMP per process
#SBATCH -J aloca-1-cpu
#SBATCH --time=01:02:00        : In case of you don't specify, the default limit is 8 hours. The maximum limit is 192 hours.
#SBATCH --mem-per-cpu=24042     :24 GB of RAM per CPU. Maximum of 480,000 for all CPUs.

#### OpenMP Settings:

export OMP_NUM_THREADS=1
export MKL_NUM_THREADS=1
export OMP_PLACES=threads
export OMP_PROC_BIND=spread
echo $SLURM_JOB_ID        : ID of job allocation
echo $SLURM_SUBMIT_DIR    : Directory job where was submitted
echo $SLURM_JOB_NODELIST  : File containing allocated hostnames
echo $SLURM_NTASKS        : Total number of cores for job

#### Load modules:
module avail : Lists the installed programs
module load NOME_MODULE

#### Run the application:
srun YOUR_EXECUTEFILE_WITH_PARAMETERS_AND_FLAGS

```
Examples: 
```markdown
- more modelo_job-gaussian.sh
- more modelo_job.sh
```
## Reminders
It is essential to specify the required time in a consistent and appropriate manner

If each CPU will use more than 24 GB use in the job header
```markdown
#SBATCH --mem VALUE
```

Use
```markdown
srun
``` 
to run the program within the job script submitted by sbatch.

---
## Defining How Cores (CPUs) Are Allocated
Examples for 16 cores:

```markdown
--ntasks=16 : Using MPI, without worrying about core distribution
and to allocate 16 independent processes (without communication)

--ntasks=16 --ntasks-per-node=1 or --ntasks=16 --nodes=16 : To allocate 16 cores distributed across different nodes

--ntasks=16 --nodes=16 --exclusive : To allocate 16 cores distributed across different nodes, without interference from other jobs

--ntasks=16 --ntasks-per-node=2 : For 16 processes distributed across 8 nodes (2 processes per node)
--ntasks=16 --ntasks-per-node=16 : For 16 processes on the same node 

--ntasks=1 --cpus-per-task=16 : For 1 process using 16 cores for multithreading

--ntasks=4 --cpus-per-task=4 : For 4 processes using 4 cores each for multithreading 

```
---

## Chain Jobs

You can organize a sequence of jobs so that one job starts after the completion of another. To do this, submit the first job, note the JobId, and then submit the next one with the following command:

```markdown
sbatch submit.sh --dependency=afterany:<JobId>
```
In this way, the second job will only start after the completion of the first job.

---

## Rules and Recommendations
- The aguia4 cluster supports up to 160 cores for serial and parallel jobs. For parallel jobs requiring more than 160 and up to 900 cores, use the aguia3 cluster.
- Don't run programs interactively, use the job queue system.
- Read the file /etc/instrucoes.txt for initial commands and tips on how to run jobs.
- The job limit per user is 20 jobs.
- The maximum queue time is 192 hours.
- The maximum number of CPUs per node is 20.
- Questions or problems? Send an email to hpc@usp.br.
