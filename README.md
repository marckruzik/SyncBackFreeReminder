# SyncBackFree Reminder

[SyncBackFree](https://www.2brightsparks.com/download-syncbackfree.html)  is a software that allows you to back up your folders, including automated backups.
However, some backup processes require specific actions beforehand, such as turning on an external drive or connecting to a specific Wi-Fi network. In such cases, automated backups cannot be fully implemented, affecting backup regularity.

**SyncBackFree Reminder** automatically checks if you haven't performed a backup in over a week and (in case you forget) launches SyncBackFree, allowing you to configure your setup and start your backup.

Technically, this is a simple C# notebook (Polyglot Notebook) that verifies if any SyncBackFree profile has not been executed in the past seven days.

## Installation
The code runs inside a Polyglot Notebook, executed using the dotnet tool **dotnet-repl** and the **Task Scheduler**, when the user logs on Windows.

### Get the repository
Clone or download the repository to ensure all files are available locally.

### Polyglot Notebook (optional)
If you want to edit the notebook or run it interactively in **VS Code** with the **Polyglot Notebook** extension:

https://code.visualstudio.com/docs/languages/polyglot

### Dotnet Repl
Install the dotnet tool **dotnet-repl** to launch the notebook (it works independently of Polyglot Notebook):

https://github.com/jonsequitur/dotnet-repl

Note: the task uses a modified version of this code to run the notebook.
> dotnet repl --run "E:\repo\SyncBackFreeReminder\main.dib" --exit-after-run

### SyncBackFree
Download and install SyncBackFree:

https://www.2brightsparks.com/download-syncbackfree.html

### Task
* Launch Task Scheduler (Windows + R "taskschd.msc")
* Import SyncBackFreeReminder.xml
* Edit the task (Right click on the task > Properties > Action > Edit)
* Update the Start in path to match the folder where the repository has been cloned (the folder containing main.dib)
* Click Ok

You will then need to edit the task to specify the folder where the script is: Right click on Task > Properties > tab Action > Start in > edit the path.

If you prefer to create the task yourself (instead of importing it), here are the main details:
* Launch Task Scheduler (Windows + R "taskschd.msc")
* Create a new Task
* Right click on Task > Properties
* tab General:
  * check Run with highest privileges
* tab Trigger:
  * Click New
  * Begin the task: At log on
  * Click Ok
* tab Action:
  * Click New
  * Program/script: cmd
  * Add arguments: /c start "" /min dotnet repl --run main.dib --exit-after-run
  * Start in: F:\Program\SyncBackFreeReminder
  * Click Ok

> [!NOTE]
> This code uses /min, so the cmd starts minimized. You should still see it briefly at a minimized task at the bottom of the screen.

## Logs
The script generates logs inside the log folder (which will appear next to main.dib).
