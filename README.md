# Windows Event Log Js

Native node.js module to log messages to the Windows Event Log.

## Installation

    $ npm install allenbriggs/node-windows-eventlog

## Prerequisites

You need to have a compatible Visual Studio compiler installed, e.g.:

    $ npm i -g windows-build-tools


## Usage

When using the library like this:

```js
  const EventLog = require('windows-eventlog').EventLog;
  const myeventlog = new EventLog("MyAppName");
  myeventlog.logSync("warn", "a message");
  myeventlog.logSync("a message"); // severity defaults to "info"
  myeventlog.log("error", "a message", function(err) {
    if (err) throw err;
  });
```

you will see something like this:

![2012-04-09_1007.png](http://joseoncodecom.ipage.com/wp-content/uploads/images/2012-04-09_1007.png)

### new EventLog(source)

This creates an instance of the EventLog with the given source.


### eventLog.log([severity,] message, [eventId,] callback)

This method will create an entry in the event log with the given message.

Optionally you can specify a severity a.k.a [log entry type](http://msdn.microsoft.com/es-es/library/system.diagnostics.eventlogentrytype.aspx). The possible values are "info", "warn" and "error".

Optionally you can specify an eventId a.k.a 1003

### eventLog.logSync([severity,] message[, eventId])

Same as `eventLog.log()` except that it blocks.

## How it works

This module is a native module using Windows' API function [ReportEvent](https://msdn.microsoft.com/en-us/library/windows/desktop/aa363679.aspx). 

Node.js applications using this module do not require an elevated account to log to the Windows Event Log.

## License 

(The MIT License)

Copyright (c) 2012 Jose Romaniello &lt;jfromaniello@gmail.com&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
