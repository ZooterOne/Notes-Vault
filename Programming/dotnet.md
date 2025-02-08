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
_main templates:_ `console` | `classlib` | `nunit` | `webapp` | `webapi` | `web` | `sln` | `gitignore` | `nugetconfig` | `buildprops`.

_frameworks:_ `net8.0` | `netstandard2.1`.
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
```
dotnet nuget locals --list all
```
list all local Nuget packages.
```
dotnet nuget locals --clear all
```
remove all local Nuget packages.
```
dotnet restore <solution>
```
___
### Build, test, run and publish
```
dotnet clean|build|test|run [--configuration <config>] [--project <path/project.csproj>] [--logger "<options>"]
```
clean, build, test or run a project.
_configurations:_ `Release` | `Debug`.
_logger examples:_
- `console;verbosity=detailed`
- `html;logfilename=\<file>`
```
dotnet publish [--configuration <config>]
```
publish a project.
_configurations:_ `Release` | `Debug`.