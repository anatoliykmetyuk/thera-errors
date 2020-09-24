# Usage
To run the example files, first install [Ammonite](https://ammonite.io/). To run e.g. `e1.sc`, use the following command:

`amm e1.sc`

# Example error files
- e1.sc – error in the YAML header syntax
- e2.sc – error in the variable name: non-existent top-level variable
- e3.sc – error in the variable name: non-existent non-top-level variable
- e4.sc – error in the function name: non-existent function
- e5.sc – function received an argument of incorrect type
- e6.sc – wrong number of arguments for the function
- e7.sc – invalid syntax
- e8.sc – invalid syntax
- e9.sc – invalid usage of a function `foreach`. Functions can only be used as arguments to function calls.
- e10.sc – invalid usage of a lambda – same as e9.sc

# Desired output
Error messages must be of the format similar to the Scala's error messages. The `*.template` format in the mock-ups below is a dummy file name. The idea is that if Thera gets the template from an external text file, that file's name should be used. In the examples of this repo, all of the templates come from Strings – hence we need to come up with an intelligible way to display that fact.

One option may be to display the file name of the Scala file they come from, and display the line and colon number relative to that Scala file. You can use Li Haoyi's [`sourcecode`](https://github.com/lihaoyi/sourcecode) library to obtain metadata on the Scala source being executed.

Error mock-ups:
```
-- Error: /path/to/folder/e1.template:7:8 -------
7  |    -  name: "Mercury", mass: "3.30 * 10^23" }
   |       ^
   | Syntax error in YAML header
```

```
-- Error: /path/to/folder/e5.sc:25:31 -------
25 |${foreach: ${system.planets}, foo}
   |                              ^
   | Incorrect argument type. Expected: lambda, found: string.
```

# Types of errors
1. Parser errors: fastparse errors and YAML errors
2. Evaluation errors
