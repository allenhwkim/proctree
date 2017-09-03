proctree
=========

Retrieve or display given a process tree

## Install

    `npm install -g proctree`

NOTE: this works on Mac/Linux/Unix environment which has default Unix commands `pgrep`, `ps`, and `kill`

## Functions 

  * `getProcessTree(pid)` to get process tree information
  * `getpids(pid)` to get process ids only in an array format
  * `show(pid)` to see process trees in a text format
  * `treeKill(pid)` to kill all processes in the process tree

## Usage With Bash Shell: 
    
    $ pstree 89982
      * 32034 node index.js
        * 32038 node node_modules/.bin/chromedriver --port=60397
          * 32039 /Users/allen.kim/github/webtest/node_modules/chromedriver/lib/chromedriver/ch ...
            * 32040 /Applications/Google Chrome.app/Contents/MacOS/Google Chrome --disable-backgr ...
              * 32045 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
              * 32048 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
              * 32050 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
  
## Usage With NodeJs Program
    ```
    var PsTree = require('proctree');
      
    PsTree.getProcessTree(pid); // to get process tree object
    PsTree.getPidse(pid);       // to get list of process ids
    PsTree.show(pid);           // to display process tree
    ```

## NodeJS Example: 
```
   > PsTree.getProcessTree(32034)
   Process {
     pid: '32034',
     name: 'node index.js',
     level: 0,
     children:
      [ Process {
          pid: '32038',
          name: 'node node_modules/.bin/chromedriver --port=60397',
          level: 1,
          children: [Object] } ] }

   > PsTree.show(32034)
    * 32034 node index.js
      * 32038 node node_modules/.bin/chromedriver --port=60397
        * 32039 /Users/allen.kim/github/webtest/node_modules/chromedriver/lib/chromedriver/ch ...
          * 32040 /Applications/Google Chrome.app/Contents/MacOS/Google Chrome --disable-backgr ...
            * 32045 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
            * 32048 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
            * 32050 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...

   > PsTree.getPids(32034)
     [ [ '32034' ], [ '32038' ], [ '32039' ], [ '32040' ], [ '32045', '32048', '32050' ] ]

   > PsTree.treeKill(32034)
     'killed 47673 47671 47668 47664 47663 47662 47658'
```
