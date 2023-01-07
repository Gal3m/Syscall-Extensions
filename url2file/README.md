// url2file

to compile url2file:
make

to delete the url2file ELF file:
make clean


./url2file application_name URL

// I verified these test case on the assignment 1 ubuntu and work it over ssh using MobaXterm application for windows.

/// All downloaded text file will saved in the ./tmp/ folder as index.html
/// other file such as applications will saved in the ./tmp/ folder with its name


// I verified these test case on the assignment 1 ubuntu and work it over ssh using MobaXterm application for windows.
Test Cases tried:

I have tested my url2file tool with a lot of URLs, and it worked perfectly. But if it doese not work with specefic URL, please check it with another one. 

./url2file wc https://www.cs.stonybrook.edu

./url2file vim https://www.cs.stonybrook.edu

./url2file vi https://www.cs.stonybrook.edu

./url2file ls https://www.cs.stonybrook.edu

./url2file cat https://www.cs.stonybrook.edu

./url2file head https://www.cs.stonybrook.edu

./url2file tail https://www.cs.stonybrook.edu

./url2file head -30 https://www.cs.stonybrook.edu | grep stonybrook

./url2file tail -10 https://www.cs.stonybrook.edu | grep twitter



/* gedit has a special functionality to download URLs. So to show my url2file successfully inject to the child process I used the below test case. url2file copy the input file to a new path with new random name and inject to the gedit child thread to open the copied file.*/
for testing this test case please close the gedit

./url2file gedit ./Makefile

/* for the purpose of load and execution I used this test cast. Bash connot download and execute the provided URLs. so url2file download the input URL in the background and change the tracee execve system call to the new path of downloaded file.

./url2file /bin/sh -c https://www3.cs.stonybrook.edu/~alisadeghi/ls

