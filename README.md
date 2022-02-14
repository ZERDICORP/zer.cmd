# zer.cmd :moyai:
#### A small module for organized handling of command line arguments.

## Example of usage :sheep:

<details>
  <summary>Project structure :deciduous_tree:</summary>
  
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
</details>

<details>
  <summary>Main.java</summary>
  
  ```java
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
</details>

<details>
  <summary>handlers.Handler_Example.java</summary>
  
  ```java
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
</details>

<details>
  <summary>Result :sparkles:</summary>
  
  ```
  $ javac Main.java
  $ java Main example 1 2 3
  arg: example
  arg: 1
  arg: 2
  arg: 3
  ```
</details>
