# GWAS pipeline

Date: April 2020

Last updated: 21/04/2020

Authors: Manuela Tan


## General description and purpose
Full pipeline for running a GWAS. This covers:
1. QC and data cleaning
2. Imputation
3. GWAS (basic linear or logistic regression models in plink or rvtests)
4. Optional meta-analyses
5. Results visualization

Thank you to the Laboratory of Neurogenetics group at NIH. This pipeline is largely built on theirs.

https://github.com/neurogenetics/GWAS-pipeline

Recommend looking at these websites if you are not familiar with plink.

http://zzz.bwh.harvard.edu/plink/

https://www.cog-genomics.org/plink/


# 1. QC and data cleaning

## 

First make a directory on kronos that you want to mount the RDS onto. You can call this whatever you want.

```
mkdir /data/kronos/mtan/mount_rd00pi_3
```

Then link the RDS drive to this folder on kronos. Put in your UCL username (skxxxx) 

```
sudo mount -t cifs -o user=skxxxx,noperm,domain=ad.ucl.ac.uk //ssh.rd.ucl.ac.uk/ritd-ag-project-rd00pi-hrmor79 /data/kronos/mtan/mount_rd00pi_3/
```
You will be prompted to put in your password - this is your UCL password not kronos password.

You will then be able to access the RDS folders from kronos. You only need to do this once.

## Copy files from the RDS onto kronos

Once you have mounted the RDS onto kronos in your directory, copying files from RDS to kronos is the same as copying files within kronos.

This is much quicker than copying files from 

```
cp /data/kronos/mtan/mount_rd00pi_3/NeuroChip_rawdata/file1.txt 
cp /data/kronos/mtan/mount_rd00pi_3/NeuroChip_rawdata/file2.txt
cp /data/kronos/mtan/mount_rd00pi_3/NeuroChip_rawdata/file3.txt 
/data/kronos/mtan/newlocation
```

## Copy files from kronos to the RDS

To copy files from kronos onto the RDS, make sure you have mounted the RDS onto kronos in your folder.

First make a directory in the mounted drive where you want to copy files into.

```
mkdir /data/kronos/mtan/mount_rd00pi_3/DESTINATION
```

Use rsync to copy files from kronos to the RDS mounted drive. Remove --dry-run once you know it works as expected.

```
rsync -vahP /data/kronos/mtan/SOURCE/ /data/kronos/mtan/mount_rd00pi_3/DESTINATION/ --dry-run
```

 
