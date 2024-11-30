### Create a solution
```
dotnet new sln <solution>
```
create a new solution.
```
dotnet sln add <path/project.csproj>
```
add a project to the solution.
___
### Create a project
```
dotnet new list
```
list all templates.
```
dotnet new install <template>.Templates
```
install a new template.
```
dotnet new <template> [--framework <framework>] [-o <project>]
```
create a new project using the given template.
_main templates:_
_- console_
_- classlib_
_- nunit_
_- webapp|webapi|web_
_- sln_
_- gitignore_
_- nugetconfig_
_- buildprops_
_frameworks: net8.0 | netstandard2.1_
___
### Packages and references
```
dotnet list package
```
list all the packages.
```
dotnet add package <package> [-v <version>]
```
add a package to the project.
```
dotnet remove package <package>
```
remove a package from the project.
```
dotnet add reference <path/project.csproj>
```
add a local project reference to the project.
___
### Build, test, run and publish
```
dotnet clean|build|test|run [--configuration <config>] [--project <path/project.csproj>] [--logger "<options>"]
```
clean, build, test or run a project.
_configurations: Release | Debug_
_logger examples:_
_- console;verbosity=detailed_
_- html;logfilename=\<file>_
```
dotnet publish [--configuration <config>]
```
publish a project.
_configurations: Release | Debug_