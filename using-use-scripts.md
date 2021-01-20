# Conda envs and Hubzero use scripts

On hubs these days we can employ conda envs to manage our Python packages, and we have long had hubzero 'use' scripts. This page will show you how use scripts help you access conda envs from Python and from Jupyter Notebooks.

Use scripts are much like [lmod](https://lmod.readthedocs.io/en/latest/) 
scripts. They set paths to specified software so you can run it. 

Use scripts can specify a path to a conda env. So, when you run the corresponding use script, all the packages installed in the env become available for you to import and call.

Here we assume you are running: anaconda-6; debian10 container.

## Conda envs: Workspace10

To use a conda env on the hub, start a Workspace10 tool. 
On the command line, type the following commands to set the anaconda installation in your path:
```
    source /etc/environ.sh
    use anaconda-6
```

Next, type this command to show the available envs:

```
    conda info --envs
```
    
Then you can activate a specific env and use it in the Workspace:    
```
    conda activate <envname>
```

If you then type 'python', you can then import and use the packages installed in the newly activated env on the python command line.

## Use scripts

Use scripts, specific to hubzero, set paths to software so you can run it.

They can enable access to various packages, including Python packages installed
in conda envs. Not all use scripts interoperate with one another.

We've named all use scripts connected with Python envs so they can be
identified easily. They have a common anaconda_6 suffix (e.g. pyproj_anaconda_6).

### List available use scripts

To list all the use scripts that are available:
```
    source /etc/environ.sh
    use 
```

### Call a use script: in notebook

To enable a conda env's packages from a Jupyter notebook, 
we first call the appropriate use script.

Use scripts enable us to gain access to the packages installed in
envs.

Enable the env with a use script, in a Jupyter notebook:
```
    import hublib.use
    %use <scriptname>
```
Note that you must import the hublib package in order to 
employ the "use" magic (%) shown here. 

Now you can import and use Python packages supplied by the 
env in question. (Need more package installs? Let us know.)

### Where the use scripts live

They are listed under /apps, in the current container subdirectory.
For debian10, that's: 
    `/apps/share64/debian10/environ.d`

Bear in mind that they may need tweaks. Tell Jeanette if you aren't
getting all the needed paths set (we have learned about this stuff
on the street, mostly).

## Some quick conda tips

This isn't specialized information, but it can come in handy.

Note that creating an env is an administrator action. If you need a new env, 
enter a ticket or get in touch with Jeanette.

### What envs are available?

Show the names of all available envs for the current container:

`conda info --envs`

### What packages are in this env?

If you have an env enabled currently, to list packages there:

`conda list`

Or for an arbitrary env, someenv:

`conda list -n <someenv>`
    
### Export your conda env

To export an env package install recipe to a .yml file:
```
    conda activate <envname>
    conda env export > <filename>.yml
```
### Turn a yml export into an env

To create an env with packages specified in a .yml file:

`conda env create -f <environment>.yml`

...then you can activate it and use it

### More
        
More conda-related tricks can be found here:

Manage [packages](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html) with conda

Manage
[environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) with conda 
