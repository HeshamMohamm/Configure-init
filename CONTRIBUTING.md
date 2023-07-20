# Contributing to RF-PHY

This project aims to simplify and guide the way beginners make their first contribution. If you are looking to make your first contribution, follow the steps below.

# Standard Operating Procedure

## Initial setup (done once)
1. Open [Analog-Devices-MSDK GitHub Page](https://github.com/Analog-Devices-MSDK) in a browser
2. Find the repository of interest (for example, [msdk](https://github.com/Analog-Devices-MSDK/msdk))
3. Fork repository (create a copy of the repository in your personal GitHub account)
4. Close Forked repository from GitHub account to personal computer with GitHub Desktop

## Terminology (based on forked repository)
1. 'upstream' refers to Analog-Devices-MSDK GitHub page
2. 'origin' refers to your personal repository, identified as {GIT USER}

## Development flow
1. In GitHub.com online, create branch on Analog-Devices-MSDK/RF-PHY-closed (or have SW team create) for new development
2. GIT pull Analog-Devices-MSDK/RF-PHY-closed/{branch} (upstream) to your computer
```
git remote add upstream https://github.com/Analog-Devices-MSDK/RF-PHY-closed.git (if not already done)
git pull upstream {branch}
git checkout {branch}
```
3. GIT push from your computer to your personal repository {GIT USER}/RF-PHY-closed/{branch} (origin)
```
git push -u origin {branch}
````
4. Modify firmware (to resolve problem statement) <br>
   a. Document the firmware as much as possible so the next developer will know what can and cannot be modified
5. GIT push changes from your computer to your personal respository as backup.
```
git push
```
6. Once development is stable, generate a pull request from GitHub.com online <br>
   a. Generate a pull request from {GIT USER}/RF-PHY-closed/{branch} to Analog-Devices-MSDK/RF-PHY-closed/{branch} <br>
   b. In generating the pull request, invite others to review.  Once comments have been addressed, GIT merge pull request. <br>
   c. Generate a CI (continuous integration) test to verify change (software team can help and implement) <br>
   d. Generate CI test result formatting (to easily explain how the modification fixed the issue) and single pass/fail condition <br>
7. Once CI passes, SW team will merge {branch} into main and rerun CI to verify nothing changed.

<img align="right" src="https://github.com/Analog-Devices-MSDK/RF-PHY-closed/blob/main/docs/CONTRIBUTING/RFteam_GIT_flow.PNG" alt="GIT flow"/>

<br clear="right"/>
<br clear="right"/>

# Setup

## Maxim MicroSDK ARM Toolchain

Use this to install NEW MicroSDK OpenOCD and the ARM GNU toolchain.

[MicroSDK ARM Toolchain](https://www.analog.com/en/design-center/evaluation-hardware-and-software/software/software-download.html?swpart=sfw0010820a)

Add the location of the ARM GNU, OpenOCD, and MinGW64 tools to the Windows Path environment variables:
```
Windows search → environment variables → user variables
Select Path → Edit...
New → Browse...
The arm-non-eabi-* tools path is C:/MaximSDK/Tools/GNUTools/10.3/bin
The MinGW64 tools path is C:/MaximSDK/Tools/MSYS2
The OpenOCD tools path is C:/MaximSDK/Tools/OpenOCD
```

## Install Git tools

Install official tool.

https://git-scm.com/download/win

Git documentation.

https://git-scm.com/book/en/v2

Creating branches.

https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging

<br clear="right"/>

## [Setup GitHub](https://help.github.com/articles/set-up-git/) if this if your first time using GitHub.

If not already done, create account on [GitHub](https://github.com)

SSH keys are required for the msdk submodules.

<br clear="right"/>

## Create GitHub directory for local storage

Typically, **C:\Users\LAPTOP_USERNAME\GitHub**

Note, if the location is LAPTOP_USERNAME\Documents\GitHub or LAPTOP_USERNAME\OneDrive..., Microsoft OneDrive will constantly sync.

This will greatly slow operation.  If data is pushed to GitHub as a standard practice, the data will be backed up. 

<br clear="right"/> 

## Download GitHub Desktop

### [Download and Install GitHub Desktop](https://desktop.github.com/)

<br clear="right"/>

## Fork the Analog-Devices-MSDK repositories

The repositories need to be forked to isolate expiremental code from the Analog-Devices-MSDK repository.
This will reduce confusion reducing the large number of branches that can be created and the lack of removing old branches in the final MSDK.

Fork this repository by clicking on the fork button on the top of this page.
<br clear="right"/>
This will create a copy of this repository in your GitHub (cloud) account.
<br clear="right"/>

<img align="right" width="300" src="https://github.com/Analog-Devices-MSDK/RF-PHY-closed/blob/main/docs/CONTRIBUTING/GitHub_fork.png" alt="fork this repository" />

### [Fork the MSDK online](https://github.com/Analog-Devices-MSDK/msdk)
### [Fork the RF-PHY-closed online](https://github.com/Analog-Devices-MSDK/RF-PHY-closed)

<br clear="right"/>

## Clone the Forked repositories

To remove confusion, your forked msdk will be stored in **msdk-fork** on your local computer.

### From GitHub Desktop:

Clone the forked repository to your machine. Go to your GitHub account, open the forked repository, click on the code button and then click the _copy to clipboard_ icon if the URL is not known.

<img align="right" width="300" src="https://github.com/Analog-Devices-MSDK/RF-PHY-closed/blob/main/docs/CONTRIBUTING/GitHub_clone.png" alt="clone this repository" />

Clone the msdk repository. We will need it to build the applications we will use with this repository.
```
File -> Clone Repository...
  URL        -> git@github.com:/GITHUB_USERNAME/msdk-fork.git
  Local Path -> C:\Users\LAPTOP_USERNAME\GitHub\msdk-fork
```

Clone the RF-PHY-closed repository. We will need it to build the applications we will use with this repository.
```
File -> Clone Repository...
  URL        -> git@github.com:/GITHUB_USERNAME/RF-PHY-closed.git
  Local Path -> C:\Users\LAPTOP_USERNAME\GitHub\msdk-fork\Libraries\RF-PHY-closed
```

Give alias to repository to reduce confusion between ADI msdk and forked msdk
```
Current repository (pulldown) -> Right click repository -> Change alias -> Change to <repository>-fork
```

<br clear="right"/> 

### Or CLI from a terminal (Powershell/Git Bash/MinGW):

```
cd C:\Users\LAPTOP_USERNAME\GitHub
git clone --recursive git@github.com:GITHUB_USERNAME/msdk-fork.git
cd msdk-fork/Libraries
git clone git@github.com:GITHUB_USERNAME/RF-PHY-closed.git
```

<br clear="right"/>

## Clone the msdk-internal repository

msdk-internal is only used for history and internal tools, it does not need to be forked since it will be read-only.

### From GitHub Desktop:

```
File -> Clone Repository...
  URL        -> git@github.com:Analog-Devices-MSDK/msdk-internal.git
  Local Path -> C:\Users\LAPTOP_USERNAME\GitHub\msdk-internal (or \msdk-fork\msdk-internal)
```

### Or CLI from a terminal (Powershell/Git Bash/MinGW):

```
cd (either /GitHub or /GitHub/msdk)
git clone git@github.com:Analog-Devices-MSDK/msdk-internal.git
```

In msdk-internal is the BTLE-TS (BTLE TestSuite).  This contains tools and test scripts for analysis.

***GDB tools are located under msdk-internal\BTLE_TS\src\tools\GDB***
```
Open msdk-internal\BTLE_TS\src\tools\GDB\.gdbinit and follow the instructions
```

To enable the GDB scripts, modify the tasks.json in your C:\Users\LAPTOP_USERNAME\GitHub\msdk-fork\Examples\ directory
<br clear="right"/> 
The .\vscode\tasks.json to include the GDB scripts should look like the code below
```
"label": "gdb (m4)",
"type": "shell",
"command": "arm-none-eabi-gdb",
"args": [
   "--ex=\"cd ${workspaceFolder}\"",
   "--se=\"build/${config:program_file}\"",
   "--symbols=build/${config:symbol_file}",
   "--ex=\"target remote localhost:3333\"",
   "--ex=\"monitor reset halt\"",
   "--ex=\"source C:/Users/LAPTOP_USERNAME/GitHub/msdk-internal/BTLE_TS/src/tools/GDB/.gdbinit\"",
   "--ex=\"b main\"",
   "--ex=\"c\""
],
```

Note: set_me is a script that prepares register access per ME part (ME14/ME17/ME18)
```
set_me can be set in .gdbinit
set_me can be set in tasks.json
   "--ex=\"source C:/Users/LAPTOP_USERNAME/GitHub/msdk-internal/BTLE_TS/src/tools/GDB/.gdbinit\"",
   "--ex=\"set_me 3\"",
   "--ex=\"b main\"",
or set manually in GDB by typing set_me ...
```

<br clear="right"/> 

## Create a branch (Only in personal GitHub account)

### From GitHub Desktop:
```
Verify repository -> Current repository (pulldown) (...RF-PHY-closed)
To create a branch: Branch -> New branch...
To switch branches: Current branch (pulldown) -> select branch
```

### Or CLI from a terminal (Powershell/Git Bash/MinGW):
Use the `git switch` command:

```
cd RF-PHY-closed-fork
git switch -c your-new-branch-name
```

For example:

```
git switch -c update_RX_timing
```

<br clear="right"/> 

## Building

You will have to re-build the library before rebuilding the applications. This will automatically copy the updated library into `msdk/Libraries/BlePhy`

```
cd /msdk-fork/Libraries/RF-PHY-closed/MAX32665/build/gcc
make
```

You can add this target to the applicaiton Makefile to automatically rebuild and copy libphy.a. _Note the indent must be a tab_

```
.PHONY:libphy

libphy:
     $(MAKE) -C ${LIBS_DIR}/RF-PHY-closed/${TARGET_UC}/build/gcc

-include libphy

all: libphy
     arm-...
```

<br clear="right"/> 

## VScode modifications

Modify Preferences (shift+ctrl+p): Preferences: Open User Settings (JSON)
```
{
    // There may be other settings up here...
        
    //"MAXIM_PATH":"C:/MaximSDK",
    "MAXIM_PATH":"C:/Users/LAPTOP_USERNAME/GitHub/msdk-fork",
    
    "update.mode": "manual",
    "extensions.autoUpdate": false,
    "workbench.startupEditor": "none",
    "files.eol": "\n",
   
    // and/or other settings down here...
}
```

If using VScode, open a folder from the msdk-fork\Examples directory, not the MSDK root folder
Because the global variable MAXIM_PATH is set to C:\MAXIM_SDK, the .vscode\settings.json file needs modification
1. Edit .vscode\settings.json
2. Remove
``` 
    "OCD_path":"${config:MAXIM_PATH}/Tools/OpenOCD",
    "ARM_GCC_path":"${config:MAXIM_PATH}/Tools/GNUTools/${config:v_Arm_GCC}",
    "xPack_GCC_path":"${config:MAXIM_PATH}/Tools/xPack/riscv-none-embed-gcc/${config:v_xPack_GCC}",
    "Make_path":"${config:MAXIM_PATH}/Tools/MSYS2/usr/bin",
```
3. Add (in place of removed lines)
```
    "MAXIM_PATH":"C:/Users/LAPTOP_USERNAME/GitHub/msdk-fork",
    "TOOLCHAIN_PATH":"C:/MaximSDK/Tools",

    "OCD_path":"${config:TOOLCHAIN_PATH}/OpenOCD",
    "ARM_GCC_path":"${config:TOOLCHAIN_PATH}/GNUTools/${config:v_Arm_GCC}",
    "xPack_GCC_path":"${config:TOOLCHAIN_PATH}/xPack/riscv-none-embed-gcc/${config:v_xPack_GCC}",
    "Make_path":"${config:TOOLCHAIN_PATH}/MSYS2/usr/bin",
```

Note:  Only use forward slashes '/' when setting this path!

<br clear="right"/> 

## Make necessary changes and commit those changes

**From GitHub Desktop:**
GitHub Desktop should automatically pull the status.

Use the Current repository pulldown to view changes.
Any repository that has a blue dot contains a modification.
Any repository that has an arrow has a change in GitHub and needs to be fetched.

To fetch, use the **Current repository** pulldown and use the **Fetch origin** pulldown.

<br clear="right"/>

**Or CLI from a terminal (Powershell/Git Bash/MinGW):**

If you go to the project directory and execute the command `git status`, you'll see there are changes.

Add those changes to the branch you just created using the `git add` command:

```
git add MAX32655/pal_bb_ble.c
```

Now commit those changes using the `git commit` command with message '-m`:

```
git commit -m "Updating RX timing parameters."
```

<br clear="right"/> 

## Push changes to GitHub

**Or CLI from a terminal (Powershell/Git Bash/MinGW):**

Push your changes using the command `git push` to `origin`: <br>
`-u` is needed if origin does not contain branch name

```
git push -u origin <add-your-branch-name>
```

replacing `<add-your-branch-name>` with the name of the branch you created earlier.

<br clear="right"/> 

## Submit your changes for review

<img align="right" width="500" src="https://github.com/Analog-Devices-MSDK/RF-PHY-closed/blob/main/docs/CONTRIBUTING/GitHub_pull_request.png" alt="Create Pull Request" />

In your for of the repository on GitHub, you'll see a `Compare & pull request` button. This will create a pull request in the base repository.

<br clear="right"/>

## Workflows

<img align="right" width="500" src="https://github.com/Analog-Devices-MSDK/RF-PHY-closed/blob/main/docs/CONTRIBUTING/GitHub_workflow.png" alt="PR Workflows" />

Workflows will atomatically run when the pull request is created. They will verify the modifications being proposed. 

<br clear="right"/>
<br clear="right"/>

<img align="right" width="600" src="https://github.com/Analog-Devices-MSDK/RF-PHY-closed/blob/main/docs/CONTRIBUTING/GitHub_workflow_buld.png" alt="Workflow artifacts" />

The `build.yml` workflow will upload an artifact of the BLE_fcc and BLE5_ctr applications that can be used for additional testing.

## Merging

**DO NOT** merge PRs into the main branch. Let the admins manage the final step.

<br clear="right"/>

## References

Base repository with instructions on how to install the necessary tools.
https://github.com/Analog-Devices-MSDK/msdk

RF-PHY-closed repository.
https://github.com/Analog-Devices-MSDK/RF-PHY-closed

msdk-internal repository for history and internal tools.
https://github.com/Analog-Devices-MSDK/msdk-internal

Instructions fow how to use VS Code with msdk.
https://github.com/Analog-Devices-MSDK/VSCode-Maxim
