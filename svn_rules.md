this is draft of rules written by kazu.

## Directories ##
  * branches/
> > this is used on release. meaning of "release" is puting to Downloads.
> > branche's tree should not merge new features.
    * naming rules
> > > iwi2200-{version}-{braches-name}

  * tags/

> > this tree is used on snapshot of trunk.
> > if many feature is added and driver will be unstable,
> > svn cp trunk to tags.

  * trunk/
> > this is unstable tree. normaly commiter should use this when commiter edit and
> > add new feature .
> > there are 3 trees( iwi2100 iwi2200 iwi3945).


## Commiting Rules ##
  * log message must be written when commiter commit.
  * log message must be understandable for all commiter.
  * current trunk is compilable when  commit.
  * if happen conflict on commiting, commiter must not **remove and add** and must fixed it by hand ( it is common rules in cvs and svn )
  * binary package and binary must not commit as basis.

## svn https commit setup ##

> when using a svn client add the line "https://iwidarwin.googlecode.com/svn" to the client preferences settings.
without this commit to https fails (the default is http).


## about issues ##
  * issues is written in single feature.

  * discussion  should be written in google groups about project managiment or large plan for futures.
