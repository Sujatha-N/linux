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

# Assignment 4

I and Veena collaborated for Assignment 4 and below are our contributions listed.

Q1. 1.	For each member in your team, provide 1 paragraph detailing what parts of the lab that member 
implemented / researched. (You may skip this question if you are doing the lab by yourself).

Ans.
## Team Members:
1. Sujatha Nadimpalli - 014686113
2. Veena Mamidi - 015226198


## Veena's Contribution:
1. I took existing Assignment-3 code and started the inner VM and ran the code for CPUID 0x4FFFFFFD. The output showed exit counts for different exit reasons and took the screenshots. Then I ran the dmesg command in the outer VM and noted that total exits count.

## Sujatha's Contribution:
1. I shut down the inner VM, removed the 'kvm_intel' module using the command 'rmmod kvm_intel'. Then changed the configuration for shadow paging using the command 'sudo insmod /lib/modules/5.16.0-rc1+/kernel/arch/x86/kvm/kvm-intel.ko ept=0'.
2. After that I have started the inner VM and executed the code to read exit count for different exit reasons. Then executed the dmesg command in the outer VM to get the total exit count.

Q2. Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”.

Ans.
#Output Screenshots

## With EPT Configuration

<img width="316" alt="Screen Shot 2021-12-08 at 10 04 34 PM" src="https://user-images.githubusercontent.com/79035205/145343496-66dad879-d40d-458d-a77c-5ba8d7690b45.png">

<img width="305" alt="Screen Shot 2021-12-08 at 10 04 10 PM" src="https://user-images.githubusercontent.com/79035205/145343539-e73d4160-4618-4d41-996b-074539a1aebb.png">

<img width="187" alt="Screen Shot 2021-12-08 at 10 05 58 PM" src="https://user-images.githubusercontent.com/79035205/145343553-ae1a833b-df56-402c-b316-828d360f9036.png">

<img width="379" alt="Screen Shot 2021-12-08 at 10 03 50 PM" src="https://user-images.githubusercontent.com/79035205/145343559-9bd0fe5d-4a20-4d11-8a38-e5660ee70490.png">

<img width="378" alt="Screen Shot 2021-12-08 at 10 03 35 PM" src="https://user-images.githubusercontent.com/79035205/145343569-5149e35d-21bb-44a2-a17a-b329eb7b8933.png">

## Without EPT Configuration

<img width="440" alt="Screen Shot 2021-12-08 at 10 02 11 PM" src="https://user-images.githubusercontent.com/79035205/145343613-074db863-10ce-41a9-847c-6434229ecb6e.png">

<img width="401" alt="Screen Shot 2021-12-08 at 10 01 22 PM" src="https://user-images.githubusercontent.com/79035205/145343630-ea7bded8-c72a-4755-9adb-c469808096de.png">

<img width="360" alt="Screen Shot 2021-12-08 at 10 01 46 PM" src="https://user-images.githubusercontent.com/79035205/145343635-c89dd303-a351-4333-be62-288e6e7ac729.png">

<img width="464" alt="Screen Shot 2021-12-08 at 10 00 33 PM" src="https://user-images.githubusercontent.com/79035205/145343646-5dda12e7-6008-48f7-a23a-e09309f580ff.png">

<img width="182" alt="Screen Shot 2021-12-08 at 10 06 28 PM" src="https://user-images.githubusercontent.com/79035205/145343662-6166379f-4800-4dbb-bc91-33139bbaebdd.png">

3Q:What did you learn from the count of exits? Was the count what you expected? If not, why not?

Ans. Number of exits in shadow paging are more than the number of exits in nested paging. The count is expected because in nested paging, exits VM only when EPT violation happens. On the other hand, in shadow paging, exit can happen very often, it can exit if there is a page fault or when the VM tries to execute CR0, CR3, CR4.

4Q. What changed between the two runs (ept vs no-ept)?

Ans. What changed between them was that, the no-ept turned on more exits for each memory access. For example, load/read/write to the %cr3 register, #PF, and any TLB flush actions. In a shadow paging architecture, certain exit controls must be enabled for each memory access to operate properly. The VMM does not worry about all of these instructions in nested paging architecture since the VMM guards the second translation of each memory access. When using nested paging architecture, VMM requires the #NPF exit control to be enabled.
