# Transparent Application Functionality Extension
A Domain-Specific Language for Writing System Call Extensions

An important use of system call (or library call) interception is to extend the functionality of applications without
requiring modifications to applications. This extension may or may not be security-related. An example of a security
extension is one that limits access to files, e.g., prevents files in your home directory from being overwritten. You
will explore such extensions in this assignment.
It is silly to extend toy applications this way. So, don’t test your implementation on toy applications. For
grading, we will test against arbitrary applications, including complex applications such as gedit. Some of these
applications will create child processes, and your extension should automatically trace all of those descendant
processes.
Choose one of the following extensions for your assignment. Make sure that you read and understand each part
in detail so that you can make an informed decision that maximizes the points you get on this assignment.
 Write a ptrace-based extension that enables applications to access remote URLs as if they were local files.
For instance, using your url2file tool, I should be able to run a command such as
url2file wc https://www.cs.stonybrook.edu
to count the number of words on a web page. Before you start writing code, use strace to identify which
system calls you need to handle. For instance, many applications use stat before attempting to open a file,
so you need to intercept stat in addition to open. When an application does open an URL, your extension
should use a program such as wget to download the web page into a temporary local file. From this point,
you should arrange it so that read operations on the \file" go to this temporary file.
For full credit, get url2file to work even when the local application attempts to load or execute a file. Make
sure that you test file loading in addition to exection. (Transparent downloading and execution of remote
code is out right dangerous, so don’t do this outside of the VM you are using for this assignment.)
 Write an extension safex that sandboxes applications so that they can be executed safely. For the purposes of this assignment, you can interpret safety to apply exclusively to file accesses; you need not concern
2yourself with the safety of other types of operations, e.g., network accesses. Specifically, you can interpret
safety to mean (a) the application can open any file for reading if the file name does not appear in the file
~/.safenoread, and (b) if it opens a file for writing, a temporary copy of the file should be made, and the
application’s access redirected to this copy. You can use the library function mkstemp to create this temporary
name without making unsafe assumptions that can lead to file-name based attacks. The purpose of (b) is to
ensure that the application won’t fail because of a denial of write access.
