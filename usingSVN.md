first version -
> this is written by xkazu.

### where I should get subversion ? ###
u can get it from  http://subversion.tigris.org.
but prebuild may has the problem which u cannot connect to https repository.
if your svn command cannot connect to https, plz sea following.


### I can check out from svn repository via http and anonymously but i cannot commit ###
you cannot commit your changing with http .
at first , you check out source code via https . (or change repository to https's)
and you should edit source code.

### my svn command cannot connet https'repository ###
your svn may not support https connection.
you should build svn from source code by hand or
you should install unstable version with fink. ( it is automaticaly build )


### i dont commit my changing with "C ..". ###
commiter resolve conflict by hand in SVN and cvs.
plz read  Resolve Conflicts (Merging Others' Changes) section of http://svnbook.red-bean.com/nightly/en/svn.tour.cycle.html#svn.tour.cycle.update


### i want to merge diff of between braches  to trunk ###
you can use "svn merge".

supposed that you want to merge diff between 15 and 18 to trunk .

```
  cd trunk/<somthing> 
  svn merge -r 15:18 ../braches/<somthing> 
```

if you merge branches's diff to trunk.
```
  cd braches/<somthing> 
  svn merge -r 20:25 ../trunk/<somthing> 
```








