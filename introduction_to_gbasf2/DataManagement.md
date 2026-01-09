# Data Management

## Checking output datasets

Once the jobs are done, the output data will be stored on the grid storage elements (SEs).

Take a look at the output of you project with the command 

```bash
gb2_ds_list myfirstProject_v2
```
It will resolve the LPN `/belle/user/yourusername/myfirstProject_v2` into the list of datablocks created by your jobs.

How many files are inside the datablock?

```{important}
Files on the grid are immutable. It means, we can't rename them or change their location once they are created.

This ensures data integrity and traceability, which is important for distributed storage systems.
```

## Downloading output Ntuples 

Now, to download the output files to your local machine, use the command

```bash
gb2_ds_get myfirstProject_v2
``` 

`````{admonition} Downloading with Rucio 
:class: tip
You can test the download of the output files using Rucio with the option `--new`. 
For large datasets, Rucio is more efficient than the default data manager used by `gb2_ds_get`.
`````

## Lifetime and quota of user datasets

In the Belle II computing model, user datasets are temporary, expecting to be downloaded in local resources.

They have a default lifetime of 3 months. After that, they will be deleted from the grid storage.

```{note}
If you need to keep the datasets on the grid for a longer period, it is more suitable to use a group space. Each 
working group has a dedicated space like `/belle/group/physics/Charmonium/`.

Discuss with your WG conveners and DP liasion to get access to the group space.
```


## Replicating datasets 

In Belle II, datasets are stored on multiple storage elements (SEs) around the world.

By default, user datasets have two replicas scattered around different SEs. It may be useful to create an additional replica,
gathered in a specific SE, to improve data access performance.

To create a new replica of your output dataset, use the command 

```bash
gb2_ds_rep -d SE /belle/user/yourusername/myfirstProject_v2
```

where `SE` is the name of the target storage element. For example:
* To replicate to KEKCC, use `KEK-TMP-DISK-SE`
* To replicate to NAF, use `DESY-TMP-SE`

You can get the full list of SEs with `gb2_se_list`.

```{important}
User files can only be replicated to storage elements with TMP on the name.

* TMP stands for temporary storage, which is purged periodically.
* DATA storage elements are reserved for official production datasets.
```

After some time, check the status of the replication with 

```bash
gb2_ds_rep_status /belle/user/yourusername/myfirstProject_v2
```

Can you explain the meaning of the different columns? 

## Downloading from a specific replica

One advantage of gathering files on a particular SE is that you can download them faster, forcing 
`gb2_ds_get` to use that replica.

Use the option `--se SE_NAME` to specify the target SE. For example, to download at KEKCC:
```bash
gb2_ds_get myfirstProject_v2 --se KEK-TMP-DISK-SE
```

Check the download speed. Is it faster than before?

If no replica is available at the specified SE, the download will fail.

