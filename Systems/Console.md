# Console

This table contains methods letting you interact with the hake.me console

* [Console.AddCommand](https://hake.me/docs/systems/console#console-addcommand-name-numargs-cmd)
* [Console.RunCommand](https://hake.me/docs/systems/console#console-runcommand-cmd)
* [Console.Print](https://hake.me/docs/systems/console#console-print-text)

---

## `Console.AddCommand(name, numArgs, cmd)`​

### Arguments

* ​`name`​ - The name of the command
* ​`numArgs`​ - *optional* The number of arguments the command requires, if ignored the command will accept any number of arguments
* ​`cmd`​ - A function taking 1 argument which is a list of arguments passed to the command

### Example

```
Console.AddCommand("test", function(args)
    Console.Print("Hello, world!")
end)
Console.AddCommand("say_hi", 1, function(args)
    Console.Print("Hello " .. args[2])
end)
```

---

## `Console.RunCommand(cmd)`​

### Arguments

* ​`cmd`​ - The command you want to run as a string that you would have typed into the console

### Example

```
Console.RunCommand("echo Hello, world!")
```

---

## `Console.Print(text)`​

### Arguments

* ​`text`​ - The text to print to the console. Newlines are supported
