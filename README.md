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

![image](https://user-images.githubusercontent.com/79035205/142982010-f4b75b86-6036-4698-ae5b-8329b369580f.png)

# Assignment 3

##Steps followed are as follows:

Using the SDM Manual, I was able to identify the exit reasons that are specified and set in KVM. For the EAX value 0x4FFFFFFD and 0x4FFFFFFC, code modifications were made to the cpuid.c and vmx.c files. The Kernel was compiled and loaded using the procedures below.
1. make -j 8 modules
2. make INSTALL_MOD_STRIP=1 modules_install
3. lsmod | grep kvm
4. rmmod kvm_intel
5. rmmod kvm
6. lsmod | grep kvm
7. modprobe kvm
8. modprobe kvm_intel
9. lsmod | grep kvm.

Started the inner virtual machine and ran the test file to check the output.


##Output Screenshots

<img width="744" alt="Screen Shot 2021-11-29 at 10 38 06 PM" src="https://user-images.githubusercontent.com/79035205/143998168-7e7aeda9-e7a5-4a66-b360-d47c721c08f7.png">

<img width="740" alt="Screen Shot 2021-11-29 at 10 38 18 PM" src="https://user-images.githubusercontent.com/79035205/143998194-75eee444-1139-4c37-b6bd-e2f85265cf66.png">

<img width="738" alt="Screen Shot 2021-11-29 at 10 38 29 PM" src="https://user-images.githubusercontent.com/79035205/143998208-b7fbc4c6-e09a-4a7f-91c5-e8a6558dd7c6.png">

<img width="741" alt="Screen Shot 2021-11-29 at 10 38 48 PM" src="https://user-images.githubusercontent.com/79035205/143998230-4d2bacdb-327c-47a9-9586-3f7bf0f9fc12.png">

Question 3 
Ans: No, for some of the exits it increased at a stable rate whereas for other exits it was random increase. More exits were observed during VM reboot operation.
VM boot entails approximately 1.4 million exits.


Question 4 
Ans: Exit types 0,10,30,31,40,48 and 28 had the most frequent exits.
Exit types 29,46,47,54 and 55 had the least frequent exits.


