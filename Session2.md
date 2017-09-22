# Dchocolatey & DSC
## Rob Reynolds

Been using manual config and golden images? We can make that better.
Powershell DSC - working with that allows us to automate infrastructure

But we're missing something?
There's more than just config management though.
You need software! There's well made packages, as well as self-made exes etc...

DSC requires MSI etc. Pain in the bum.
Chocolatey is software management through PS. 

There's a community repo in the public domain. So we can't get licensed software etc.
We get past this with organisational use - internal & licensed apps.

So what's possible?
Integrates with PS and DSC. It's decentralised so you can mix & match sources.
FOSS version is just package management. 
For Business (C4B) is more complete software management system. Better for businesses!

Allows automatic uninstallation, and integrates with Chef, Puppet etc.
Has auditing features so you can see what's installed.
If you build your own repos you can even use Chocolatey to create an entry in Programs & Features in Win.
Also lets you see what packages require updating.

If you have C4B there's a package builder to make creating the packages easier.
Package synchroniser watches the state of the machine to find out what packages may have been changed outside of chocolatey, or are required.

On the roadmap - Central management dashboard, windows Nano support, and becoming an official PS package provider.

There's a Choco DSC resource you can install to allow DSC to install and use Chocolatey.
If you're working with custom packages you'll need a package manager locally to act as a repo. Chocolatey provide their own repo server.

