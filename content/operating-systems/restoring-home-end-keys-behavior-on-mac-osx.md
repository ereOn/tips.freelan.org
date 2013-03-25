Title: Restoring home/end keys behavior on Mac OSX
Date: 2013-03-25
Category: Operating systems
Tags: mac-osx

For people who, like me, come from a Windows and/or Linux world, switching to Mac OS X can be an unpleasant adventure (at least at first).

One of the things that bothers me the more is the default behavior of the home/end keys: they basically do the same as the page-up/page-down keys which, imho, is completely dumb.

I don't want to use Command-Left/Command-Right (the recommended way) because, well, I have some muscle-memory, I still have to work on Windows and Linux workstations and I want to keep my sanity.

Luckily enough, that's easy to fix.

Open a terminal and type:

> mkdir ~/Library/KeyBindings
> vim ~/Library/KeyBindings/DefaultKeyBinding.dict

And make sure the file has the following content:

    {
    	/* Remap Home / End to be correct :-) */
    	"\UF729"  = "moveToBeginningOfLine:";                   /* Home         */
    	"\UF72B"  = "moveToEndOfLine:";                         /* End          */
    	"$\UF729" = "moveToBeginningOfLineAndModifySelection:"; /* Shift + Home */
    	"$\UF72B" = "moveToEndOfLineAndModifySelection:";       /* Shift + End  */
    }

And here it goes !
