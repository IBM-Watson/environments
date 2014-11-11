# IBM Watson Development Environments

In order to provide consistent development environments, we have created a [Vagrant](https://www.vagrantup.com/) powered virtual machine to simplify setup and reduce potential machine configuration errors. These machines work across Windows, OS X, and Linux machines, ensuring developers on any operating system can all develop in a consistent way.

## Requirements

All of the virtual machines require the following to be installed. All requirements have downloadable installers, so no fumbling with the command line needed.

* [Vagrant](https://www.vagrantup.com/downloads.html)
* [Virtual Box](https://www.virtualbox.org/wiki/Downloads)
* [Git 2.0](http://git-scm.com/downloads)

It is also recommended you register for a [GitHub](https://github.com/) account, follow the [first-time Git setup](http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) instructions, and [add an SSH key to Git](https://github.com/settings/ssh). This will ensure that your machine is ready and able to interface with Git on the virtual machines.

### Windows Users

While our virtual machines will work on Windows machines only following the above steps, it is recommended the following steps are also performed in order to provide a more consistent command line experience.

1. Download [Console 2](http://sourceforge.net/projects/console/files/)
* Extract `Console.exe`
* Add `Console.exe` shortcut to Desktop
* Open `Console.exe`, go to `Edit->Settings` and set the shell to PowerShell (usually `C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`)
* Set the Startup dir to your User directory
* Restart `Console.exe`

This will let you access your terminal easily through **Console 2** and let you use [PowerShell](http://en.wikipedia.org/wiki/Windows_PowerShell), a much more powerful command line shell for Windows than the standard `cmd`.

## Setup

Once you have the above installed, spinning up a virtual machine is as simple as picking which environment you'd like to use, copying the contents of of the **Recommended Vagrantfile** (the part in the code block, not the exposition) into a file named `Vagrantfile` in the directory you'd like to work in, and running `vagrant up`. Remember to commit your `Vagrantfile` into your version control system.

If you have the [Watson Yeoman Generator](https://github.com/IBM-Watson/generator-watson) installed, you can call `yo watson:environment` or `yo watson:env` to scaffold out your `Vagrantfile` for you and stand up your virtual machine.

## Usage

You can edit all of the files in your working folder with your local tools, no need to change anything you do in that regard! To run commands in the virtual machine, run `vagrant ssh` in your terminal from the folder your `Vagrantfile` is in. This will bring you into your virtual machine where you can run your commands as normal. To exit your virtual machine while inside it and bring you back to your computer, run the `exit` command.

If you have a single command you would like to run inside your virtual machine from the root of your shared folder (relative to the folder your `Vagrantfile` is in), you can run `vagrant ssh -c "{{command}}"` replacing `{{command}}` with the command you would like to run. This supports interactive prompts, so Yeoman generators, Compass watch, and the like will all work and provide active feedback.

While inside your virtual machine, the default prompt is [zsh](http://www.zsh.org/) with [Oh My ZSH](https://github.com/robbyrussell/oh-my-zsh). We have written a custom theme for Oh My ZSH that is on by default.

## Provisioning

If you would like to add additional provisioning on top of an environment, keep in mind that it will run through an interactive ZSH prompt that does start by sourcing Oh My ZSH and the like.

## License

The MIT License (MIT)

Copyright (c) 2014 IBM Watson

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
