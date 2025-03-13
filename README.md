# Save Check

A simple C# notebook (Polyglot Notebook) to check if a SyncBackFree profile has not been launched since a week.

## Installation
The code is inside a Polyglot Notebook, launched with the dotnet tool dotnet-repl, when the user logs on Windows through the Task Scheduler.

### Get the repository
Clone or download the repository to have all files locally.

### Polyglot Notebook (optional)
If you want to edit the notebook, or run it as a notebook with Vs Code extension Polyglot Notebook:
https://code.visualstudio.com/docs/languages/polyglot

### Dotnet Repl
Install the dotnet tool dotnet-repl to launch the notebook (can work without Polyglot Notebook installed):
https://github.com/jonsequitur/dotnet-repl
It uses this code to run the notebook.
> dotnet repl --run "E:\repo\SaveCheck\main.dib" --exit-after-run

### SyncBackFree
Download and install SyncBackFree:
https://www.2brightsparks.com/download-syncbackfree.html

### Task
Launch Task Scheduler (Windows + R "taskschd.msc"), and import SaveCheck.xml.
Edit the task (Right click on the task > Properties > Action > Edit), and correct the starting path by choosing the folder where the repo has been cloned (the folder that contains main.dib).

## Logs
The script creates logs in the log folder (will appear next to main.dib).
