mockbuild
=========

a git integration for mock, git and rpm

you can	record this script in /usr/bin

 cp git_mockbuild /usr/bin
 chmod 775 /usr/bin/git_mockbuild

you need to make a folder with the exact name of the rpm (eg smeserver-dhcpmanager). Inside of this folder you create your git repository and work on files and folder of your RPM. Be aware that GIT do not track empty repositories, you have to create a '.gitignore' (even with nothing inside) in each empty directory, if you want they will be incorporated in your GIT repository.

you can	use this command line in case of many folders and subfolders

 find * -type d -empty -exec touch {}/.gitignore \;

Once you want to make the RPM then simply use git_mockbuild without arguments in the root folder of your git repository, the architecture of build come from the spec file. But if needed you can  choose another build arch. You have to choose one argument.

 git_mockbuild
or
 git_mockbuild sme8-i386 sme8-x86_64 sme9-i386 sme9-x86_64

by default if the build architecture is not specified in the spec file, it is the case of packages which are not 'noarch', the RPM will be make by mock with the same architecture of your build server. Therefore you have to specify which arch you want if you need another rpm architecture (eg i386 instead of x86_64)

The CentOS target version comes from the GIT branch you created in your GIT repository. For example if your branch is named sme9 then the build is done for el6, else the target CentOS version is el5.

For an automatic build for all architectures you should take considerations about Plague which is done for that.

Each time you execute the script, the GIT branch in use is tagged with the version of the RPM.



