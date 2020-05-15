# Conda envs and Hubzero use scripts

On hubs these days we can create conda envs, and we
have long had hubzero 'use' scripts. 

Use scripts are much like module-load scripts. They
set paths to specified software so you can run it. 

Lately we've been setting the use scripts up 
with the paths that match a conda env. So when you
run the use script, the paths are all there as if
you were inside the conda env. 

Here we assume: anaconda-6; debian7 container.

## Conda envs: Workspace

To get set up to use a conda env, start a hub Workspace. 
Then, on the command line you should see the available envs
associated with the anaconda-6 install:
```
    source /etc/environ.sh
    use anaconda-6
    conda info --envs
```
    
Then you can activate the env and use it in the Workspace:    
```
    conda activate <envname>
```

## List available use scripts

Note: not all use scripts interoperate with one another.
We've named all anaconda-6 use scripts so they can be
identified (e.g. pyproj_anaconda_6).

```
    source /etc/environ.sh
    use 
```


## Enable a use script: in notebook

Enable the env with a use script, from a Jupyter notebook:
```
    import hublib.use
    %use <scriptname>
```

## Where the use scripts live

They will be listed under /apps, in the current container subdirectory.
For debian7, that's: 
`/apps/share64/debian7/environ.d`

Bear in mind that they may need tweaks. Tell Jeanette if you aren't
getting all the needed paths set (we have learned about this stuff
on the street, mostly).
    
## Export your conda env

This isn't specialized information, but it sure is handy.

To export env package install recipe to a .yml file:
```
    conda activate <envname>
    conda env export > <filename>.yml
```
## Turn a yml export into an env

`conda env create -f <environment>.yml`

...then you can activate it, 

## What packages are there?

`conda info --envs`
        
More conda-related tricks can be found here:
Manage packages (see also, Manage environments):
https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html
https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html
