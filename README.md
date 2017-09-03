proctree
=========

Retrieve or display given a process tree

## Install

    `npm install -g proctree`

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
   > var PsTree = require('./index');
   undefined
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
```
