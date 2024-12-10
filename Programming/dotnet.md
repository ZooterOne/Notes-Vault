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
- _console_
- _classlib_
- _nunit_
- _webapp|webapi|web_
- _sln_
- _gitignore_
- _nugetconfig_
- _buildprops_
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
- _console;verbosity=detailed_
- _html;logfilename=\<file>_
```
dotnet publish [--configuration <config>]
```
publish a project.
_configurations: Release | Debug_