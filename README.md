# cmpe 283 Assignment 2
##D one by Sujatha Nadimpalli

## Steps followed are as follows:
1. Forked the linux tree
2. Cloned the repo into an Ubuntu machine
3. Downloaded required packages for building kernel.
4. Executed the command 'sudo cp /boot/{config-name} ./.config
5. Executed 'sudo make oldconfig'
6. Edited cpuid.c and vmx.c files to satisfy the first two requirements mentioned in the assignment.
7. Executed `sudo make -j 8 modules`
8. Executed `sudo make -j 8`
9. Executed `make INSTALL_MOD_STRIP=1 modules_install`
10. Loaded kvm using the command `modprobe kvm` and `modprobe kvm_linux`
11. Created nested vm with virtual machine manager
12. Created a test file and executed to see the ouput.

file:///home/himaja/Downloads/Screenshot%20from%202021-11-22%2022-24-48.png![image](https://user-images.githubusercontent.com/79035205/142981474-af563738-5a78-47b3-875a-25aea8931e02.png)
