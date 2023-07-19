# Contributing to RF-PHY

This project aims to simplify and guide the way beginners make their first contribution. If you are looking to make your first contribution, follow the steps below.

#### [Setup Git](https://help.github.com/articles/set-up-git/) if this if your first time using GitHub.

SSH keys are required for the msdk submodules.

## Fork this repository

<img align="right" width="300" src="https://user-images.githubusercontent.com/54692400/189542489-bdae004a-1cfe-42ff-9fd5-108447c198fb.png" alt="fork this repository" />

Fork this repository by clicking on the fork button on the top of this page.
This will create a copy of this repository in your account.

<br clear="right"/>

## Clone the repositories

Clone the msdk repository. We will need it to build the applications we will use with this repository.

```
git clone --recursive git@github.com:Analog-Devices-MSDK/msdk.git
```
<br clear="right"/>

<img align="right" width="300" src="https://user-images.githubusercontent.com/54692400/189542589-1fb9f6f3-11fa-4084-b8f0-219a9b2b4c0b.png" alt="clone this repository" />

Now clone the forked repository to your machine. Go to your GitHub account, open the forked repository, click on the code button and then click the _copy to clipboard_ icon.

```
cd msdk/Libraries
git clone git@github.com:<this-is-you>/RF-PHY-closed.git
```

Where `<this-is-you>` is your GitHub account name.

## Create a branch

Now create a branch using the `git switch` command:

```
cd RF-PHY-closed
git switch -c your-new-branch-name
```

For example:

```
git switch -c update_RX_timing
```

## Building

You will have to re-build the library before rebuilding the applications. This will automatically copy the updated library into `msdk/Libraries/BlePhy`

```
cd MAX32665/build/gcc
make
```

You can add this target to the applicaiton Makefile to automatically rebuild and copy libphy.a. _Note the indent must be a tab_

```
.PHONY:libphy

libphy:
        $(MAKE) -C ${LIBS_DIR}/RF-PHY-closed/${TARGET_UC}/build/gcc

-include libphy

all: libphy
```

## Make necessary changes and commit those changes

If you go to the project directory and execute the command `git status`, you'll see there are changes.

Add those changes to the branch you just created using the `git add` command:

```
git add MAX32655/pal_bb_ble.c
```

Now commit those changes using the `git commit` command:

```
git commit -m "Updating RX timing parameters."
```

## Push changes to GitHub

Push your changes using the command `git push`:

```
git push origin -u <add-your-branch-name>
```

replacing `<add-your-branch-name>` with the name of the branch you created earlier.

## Submit your changes for review

<img align="right" width="500" src="https://user-images.githubusercontent.com/54692400/189543654-46f9196a-3ad4-4a8f-aea2-3b8c78ba21dc.png" alt="Create Pull Request" />

In your for of the repository on GitHub, you'll see a `Compare & pull request` button. This will create a pull request in the base repository.

<br clear="right"/>

## Workflows

<img align="right" width="500" src="https://user-images.githubusercontent.com/54692400/189545355-d46e2894-a82a-42cc-aec4-df687ec90525.png" alt="PR Workflows" />

Workflows will atomatically run when the pull request is created. They will verify the modifications being proposed. 

<br clear="right"/>

<img align="right" width="600" src="https://user-images.githubusercontent.com/54692400/189546277-14719d8a-3242-4b28-b824-629095d4b9de.png" alt="Workflow artifacts" />

The `build.yml` workflow will upload an artifact of the BLE_fcc and BLE5_ctr applications that can be used for additional testing.

<br clear="right"/>

## References

Base repository with instructions on how to install the necessary tools.
https://github.com/Analog-Devices-MSDK/msdk

Instructions fow how to use VS Code with msdk.
https://github.com/Analog-Devices-MSDK/VSCode-Maxim
