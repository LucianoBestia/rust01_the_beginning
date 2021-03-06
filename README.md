Things are changing fast. This is the situation on 2019-05-02. Luciano Bestia  
# rust01_the_beginning  
The first project in Rust. How to install the toolchain and have a first result in 5 minutes.  
There is almost always a lot of different ways to achieve some result. I will describe only one option - for simplicity.  
The learning process is easier if it is simple. But the reality is always much much more complicated then that.  
Knowledge must come in small drops to absorb it. If it is pouring it just confuses the curious mind.  
The "book" https://doc.rust-lang.org/stable/book/ is a great learning tool. The first chapters are really easy and practical and very well written. Use it.   
## Windows  
I used Windows most of my long programmers life (33 years). It is still the number one desktop OS.  
So for developing desktop apps it is a good start to have the developer environment inside Windows.  
1. Go to https://www.rust-lang.org and choose `GET STARTED`.  
2. Find the `RUSTUP-INI.EXE` (6MB) Download it.  
3. Run it. Windows Defender will warn you that the app is unrecognized. Choose `More info` and `Run anyway`. Take your responsibilities!  
4. Read the text in the console and answer with default choices. They are ok for the first time install.  
5. If you don't have `Tools for Visual Studio 2019` for C++ installed on your machine, you will get a warning by the installer and instruction what to do.  
Find the installation of C++ tools here and install it:  
https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16  
The file name is something like `vs_buildtools__1788641612.1545772962.exe`.  
It downloads the true installer with a graphical user interface.  
You have to choose 
- `C++ build tools` on the left 
- and then the latest `Windows 10 SDK xxx` on the right.  
It will download (1.2 GB) and then install (4.4 GB).  
Probably now you have to restart your PC.  
GOTO step 3.  
6. Rustup will download and install a number of tools and documentation. Be patient with the docs, they take a looong time. There is a big discussion in the Rust community to not install them by default and let the user choose them later. But now we have what we have.  
  
That's it. Rust is installed. Super simple (except for the C++ tools).  
  
## The first project  
Press `window + s` (`window` is this strange key on the keyboard in the first row near `ctrl` and `alt`) it opens the start menu.  
Start typing `command prompt` it will suggest you exactly that and press Enter to run it.  
You should be inside your user folder. For me it is `C:\Users\Luciano`.  
I created a folder with the name all small caps `/rustprojects` inside my user folder.  
In Windows file/folder names are not case sensitive, but in Linux they are very sensitive. Be careful.  
```
mkdir rustprojects
```  
```
cd rustprojects
```  
We will create a new rust project with this simple command  
```
cargo new first_hello
```  
```
cd first_hello
```  
You probably already know that you can type just `cd f` and then press the Tab key multiple times to get suggestions of subfolders name starting with `f`.  
If not, try it. It works great.  
  
For most of the commands it is really important in what folder you run them. Now you should be inside the `c:\users\Luciano\rustprojects\first_hello` folder (with your username and not mine).  
Let build the project and run it:  
```
cargo run
```  
Congratulations! You wrote your first working rust project.  
  
I am sure you want to try this again one more time.  
Press the `arrow up`. The command prompt will suggest the last typed command from history. In this moment it is `cargo run`. Run it by pressing Enter.  
This history stuff with `arrow up` and `arrow down` is super useful, because you will repeat the same commands a lot.  
This time the compilation is really fast, because there is nothing new to compile.  
## VSCode
Now you want to see and change the code. I choose the opensource editor VSCode.  
Download it and install it from here https://code.visualstudio.com/  
Run it and add a VSCode extensions for rust `Ctrl + Shift + X`:
- Rust (rls)
  
Open your project with  
`File - Open Folder... - c:\users\Luciano\rustprojects\first_hello`  
Use your username here instead of mine.  
Simple Rust projects are basically just a folder. There is a convention of subfolders names and it works just that simple. You will find your code in the `src` subfolder in the file `main.rs`.  
Change the word `Hello` into `First Hello` and save it with `Ctrl + s`.  
You already know from before how to build and run it. Give it a try and show what you have learned.  
## Git
Git is a great tool and you should use it for code versioning. Use it often and group the changes so that is easy to understand what a commit really changes.  
VSCode it totally prepared for it. I am not sure if you need to install it manually or VSCode makes all in its installation. You will quickly find out.  
The third icon on the left or `Ctrl + Shift + g` opens a simple list: what has changed. You write a `Message` and press `Ctrl + Enter` to commit.  
If you want to see the changes you select a filename. The changes will show on the right.  
You can also use it to push or sync the changes on GitHub and much more. Then there is a specific `.gitignore` file for rust source code. This is advanced stuff. You will learn it step by step.  

## WSL Windows subsystem for Linux
Most of the servers in the world today are Linux. So you want a Linux environment to develop for Linux servers. It is possible now to use WSL `Windows subsystem for Linux` inside your Windows machine. It feels just like Linux for almost everything you'll need. It is like having a virtual machine, but a little bit simpler.  
Here is how to enable it and install it:  
https://docs.microsoft.com/en-us/windows/wsl/install-win10  
I choose the Debian GNU/Linux distro. Old school.  
From WSL Linux you can use the files in Windows. But from Windows you cannot use files in WSL Linux. I want my `/rustprojects` files to be accessible from both OS.  
I create a symlink in WSL to the `/rustprojects` folder  
`ln -s /mnt/c/Users/Luciano/rustprojects ~/rustprojects`  
Now when I start Debian I am in my home user folder `~`  
`luciano@MyMachine2015:~$`  
and I can command  
`cd rustprojects`  
I am now inside the same `/rustprojects` folder as in Windows.  
The Linux bash (console) has also suggestions for subfolder names if you type `cd r` and then Tab key, but it is not so user friendly as in windows. It has also the command history with `arrow up` and `arrow down`. That is great because it remembers also the old commands from old sessions.  
  
Installing rust on Linux is simple:  
```
$ curl https://sh.rustup.rs -sSf | sh
```  
You will find this info in the "book": https://doc.rust-lang.org/stable/book/  
  
Go to the folder /first_hello  
```
cd first_hello
```  
and build and run the project  
```
cargo run
```  
Congratulations! The same project now works in Windows and also on Linux.  
  
The result is in the `/target` folder. Normally the windows file ends with `.exe` like `first_hello.exe`, but the Linux file has no extension like `first_hello`.  
If you build a project in Linux the result will be for Linux. And if you build it in Windows, the result will be for Windows. The results are binary incompatible.  
  
You can still use the Windows VSCode for editing the source code and windows Git for versioning. You then use the Debian bash just to build it and run it.  
## For the curious TL;DR;  
The user home folder is called `~` in Linux and mostly `%HOMEPATH%` in Windows.  
Windows can very often understand both \ and / as folder delimiters, but not always. In Linux there is only /. So it is smart to learn to user / everywhere where it works.  
Linux file/folder names are very very case sensitive, windows are case insensitive. That can make a lot of confusion. Try to write always small caps names if it is possible. And try to avoid spaces and strange characters. Underscore is very well understood in every situation, I recommend it.  
## Next projects
https://github.com/LucianoBestia/rust02_workspace_and_testing  
## References
https://doc.rust-lang.org/stable/book/  
  

