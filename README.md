proctree
=========

Get, display, or kill a processe tree

## Install

    `npm install -g proctree`

NOTE: this works on Mac/Linux/Unix environment which has default Unix commands `pgrep`, `ps`, and `kill`

## Functions 

  * `getProcessTree(pid)` to get process tree information
  * `getPids(pid)` to get process ids in an array
  * `show(pid)` to see process trees in text format
  * `treeKill(pid)` to kill all processes in the process tree

## Usage With Bash Shell: 
    
    $ proctree 89982
      * 32034 node index.js
        * 32038 node node_modules/.bin/chromedriver --port=60397
          * 32039 /Users/allen.kim/github/webtest/node_modules/chromedriver/lib/chromedriver/ch ...
            * 32040 /Applications/Google Chrome.app/Contents/MacOS/Google Chrome --disable-backgr ...
              * 32045 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
              * 32048 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
              * 32050 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
  
## Usage With NodeJs Program
    ```
    var proctree = require('proctree');
      
    proctree.getProcessTree(pid); // to get process tree object
    proctree.getPidse(pid);       // to get list of process ids
    proctree.show(pid);           // to display process tree
    ```

## NodeJS Example: 
```
   > proctree.getProcessTree(32034)
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

   > proctree.show(32034)
    * 32034 node index.js
      * 32038 node node_modules/.bin/chromedriver --port=60397
        * 32039 /Users/allen.kim/github/webtest/node_modules/chromedriver/lib/chromedriver/ch ...
          * 32040 /Applications/Google Chrome.app/Contents/MacOS/Google Chrome --disable-backgr ...
            * 32045 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
            * 32048 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...
            * 32050 /Applications/Google Chrome.app/Contents/Versions/60.0.3112.113/Google Chrome ...

   > proctree.getPids(32034)
     [ [ '32034' ], [ '32038' ], [ '32039' ], [ '32040' ], [ '32045', '32048', '32050' ] ]

   > proctree.treeKill(32034)
     'killed 32050 32048 32045 32040 32039 32038 32034'
```
