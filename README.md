# zer.cmd :moyai:
#### A small module for organized handling of command line arguments.

## Example of usage :sheep:

Project structure :deciduous_tree:
```
├── Main.java
├── handlers
│   └── Handler_Example.java
└── zer
    └── cmd
        ├── CMDHandler.java
        ├── CMDHandlerProcessor.java
        └── CMDPattern.java
```

First, let's create a handler that will have an annotation with the value that this handler expects from the command line.

```java
/* handlers.Handler_Example.java */

package handlers;

import zer.cmd.CMDPattern;
import zer.cmd.CMDHandler;

@CMDPattern("example 1 2 3")
public class Handler_Example extends CMDHandler
{
  @Override
  public void handle(String[] args)
  {
    for (String arg : args)
      System.out.println("arg: " + arg);
  }
}
```

Well, now it remains to create an instance of the __CMDHandlerProcessor__ class and add our handler created above to it.  
After that, we start the processor by passing command line arguments to it.

```java
/* Main.java */

import zer.cmd.CMDHandlerProcessor;
import handlers.Handler_Example;

public class Main
{
  public static void main(String[] args)
  {
    CMDHandlerProcessor processor = CMDHandlerProcessor.getInstance();

    processor.add(new Handler_Example());

    processor.process(args);
  }
}
```

```
$ javac Main.java
$ java Main example 1 2 3
arg: example
arg: 1
arg: 2
arg: 3
```
