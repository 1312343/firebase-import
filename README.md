firebase-import is a helper utility to import large JSON files into [Firebase](https://www.firebase.com/).  
It breaks the JSON into smaller chunks and then stores those chunks individually through the Firebase API.

## Installing

Install the firebase-import module globally or install it locally and add it to your path:

    $ npm install -g firebase-import

or

    $ npm install firebase-import
    $ export PATH=$PATH:`npm bin`

## Usage

    $ firebase-import
    Usage: firebase-import

    Options:
      --firebase_url, -f  Firebase URL (e.g. https://test.firebaseio.com/).                   [required]
      --json, -j          The JSON file to import.                                            [required]
      --merge, -m         Write the top-level children without overwriting the whole parent.  [boolean]
      --force             Don't prompt before overwriting data.                               [boolean]

## Example

    $ firebase-import --firebase_url https://test.firebaseio-demo.com --json test.json
    All data at https://test.firebaseio-demo.com will be overwritten.
    Press <enter> to proceed, Ctrl-C to abort.

    Reading /Users/michael/tmp/test.json... (may take a minute)
    Preparing JSON for import... (may take a minute)
    Importing [=================================================] 100% (9431/9431)
    Import completed.

Or an example of merging the contents of test.json with what's already in Firebase:

    $ firebase-import --firebase_url https://test.firebaseio-demo.com --json test.json --merge
    Each top-level child in test.json will be written under https://test.firebaseio-demo.com.  If a child already exists, it will be overwritten.
    Press <enter> to proceed, Ctrl-C to abort.

    Reading /Users/michael/tmp/test.json... (may take a minute)
    Preparing JSON for import... (may take a minute)
    Importing [=================================================] 100% (9431/9431)
    Import completed.

## LICENSE
[MIT](http://firebase.mit-license.org/).
