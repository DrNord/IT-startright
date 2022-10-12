# IT-developer: start right
:notebook: **A conspectus in 2 parts, a task with a secret and an exercise for independent work**   

:arrow_right: на русском [README-RU.md]

© 2022 Dr. Nord 

### License conditions

The exclusive copyright owner of this repository content is Dr. Nord, you are allowed to use it for personal non-commercial purposes, see [LICENSE-DN.txt] for details.

## Part I :superhero: - 7 pro's steps 
:electron: ***Turn your "I don't understand" into "I see what's what."***  
:computer: ***Master the basic tools of an IT-developer.***  
:godmode: ***Equip properly before the intricate road to the world of information technologies.***

**Watch** the [video-lesson part 1][lesson-p1].

:point_right: **Installation** of basic applications, **setting up** the information environment for IT-development.  
:point_right: **Technologies used:** systematization of accounts, symmetric and asymmetric encryption, version control, digital signatures, destruction of information.  

## Part II :deciduous_tree: - your ecosystem  
:seedling: ***Learn to form your ecosystem for IT-development.***  
:earth_africa: ***Start your way into the world of information technologies in full readiness.***

**Watch** the [video-lesson part 2][lesson-p2].

:point_right: **Installation** and **setting up** the integrated development environment and extensions.  
:point_right: **Technologies used:** syntax highlight and extended code editing possibilities, spell check, static code analysis, debugging, live server.

## Table of contents

<details>
  <summary></summary>

  [Prerequisites](#prerequisites)
  
  [Part I :superhero: - 7 pro's steps](#part1)
  - [1. Web browser and reference documentation](#browser)
  - [2. Password manager](#keepass)
  - [3. Data erase](#eraser)
  - [4. E-mails](#emails)
  - [5. Digital signature and messages encryption](#digisign)
  - [6. Online repositories](#online-repos)
  - [7. Version control](#git)
  - [Home task](#hometask)
  
  [Part II :deciduous_tree: - your ecosystem](#part2)
  - [Installation of an integrated development system](#ide)
  - [Syntax highlight](#syntax-highlight)
  - [Smart completion](#intelli-sense)
  - [Extensions](#extensions)
  - [Static code analysis](#static-analysis)
  - [Debugging (dynamic code analysis)](#debug)
  - [Built-in terminal](#terminal)
  - [Built-in version control system](#version-control)
  - [Live server](#live-server)
  - [Exercise for independent work](#exercise)
    
  [Author and contacts](#author-contacts)
</details>

## <a name=prerequisites /> Prerequisites

**Knowledge:**
  - Basic:
    - computer architecture;
    - basic operating system administration;
    - english at the beginner level - A2 according to the [Common European Framework of Reference for Languages][cefr].
  - Additional:
    - basics of digital cryptography.
    
**Skills:**
  - Basic:
    - install and configure programs;
    - organize files and folders;
    - read documentation, use programs in english;
    - use the terminal.
  - Additional:
    - memorize unmemorable information.

**Equipment:**
  - Basic:
    - a computer (laptop) with an installed operating system;
    - stable Internet connection.
  - Additional:
    - :woman_cartwheeling: yoga mat.
  
It is assumed that the Windows 10 operating system is used. However, all programs used have either an alternative or a Linux version.

*Also, you will definitely need attention and perseverance!*

## <a name=browser /> 1. Web browser and reference documentation

Install a modern browser, Opera, Mozilla Firefox or Google Chrome are good choices, Edge or Safari is also good.

Oftenly use a search engine, for example [duckduckgo][ddgo] or [google] - on the Internet today there are answers to a great many general and particular questions.

Please refer to the reference documentation periodically. For web frontend, for example, a good choice would be a reference system from [Mozilla Developer Network][mdn].

Be sure to read the user manuals for the programs you use. 

## <a name=keepass /> 2. Password manager

A password manager is used to store your Internet credentials securely and in order.
It is recommended to use password managers that store the password database locally. The [KeePass] app would be a good choice:
- create a new file - the database of your passwords;
- come up with a strong master password;
- be sure to remember it, you can also write it down and hide it securely;
- create a copy of the password database file and also hide it securely (the file and its password must be stored separately);
- use the program regularly, the more times you enter the password, the better you will remember it.

## <a name=eraser /> 3. Data erase

When you delete files and folders (even after emptying the Recycle Bin), the data remains on the disk. In fact, the operating system only marks the area where the data was stored as free. Such data is easily restored if nothing new has been written to this free area.  
Make it a rule to destroy important information in a secure way by overwriting.
The [Eraser][eraser] app successfully copes with this task.  
In the settings for the removal method, it is enough to select 1 pass.
To destroy extremely sensitive information, you can choose more intensive methods of deletion up to several dozen passes. However, remember that this way you can very quickly deplete the resource of your disk. This is especially true for SSD drives.

## <a name=emails /> 4. E-mails

Enter at least two email addresses:
- the first - for registration on Internet resources, keep it secret to protect it from password recovery attempts by an intruder;
- the second - for distribution in the public domain and communications.

Enter the credentials of your email addresses into the password manager.
Make up a pseudonym under which you can present your works on the Internet if you do not want to be published under your real name.

## <a name=digisign /> 5. Digital signature and messages encryption

Master [The GNU Privacy Guard][gpg] app (GnuPG), designed to create cryptographic key pairs and implement the functions of encryption and digital signature of electronic messages and other data.
Download the app and check the integryty of the downloaded file.
If you are downloading the program for the first time:
- calculate the checksum of the downloaded file:
```
> certutil -hashfile <filename> sha1
```
- find publications of announcements about the release of a new version of the GnuPG application on various Internet resources, in such announcements, as a rule, checksums are also published;
- compare the checksum you calculated with the published checksums, **they must match exactly**.
The more comparisons you make, the less likely you are to encounter a fake.
Detailed instructions for verifying a GnuPG application can be found on the official website.
 
Create a set of cryptographic keys:
```
> gpg --gull-generate-key --expert
```
When creating a key, you can use the default values.
- Generate a strong password in KeePass and enter it when creating a secret key;
- Save the public and private keys on disk:
```
> gpg --output public.asc --export --armor <keyID>
> gpg --output private.asc --export-private-key --armor <keyID>
```
As \<keyID\>, you can specify either a name, or an email, or an identifier, the program will find the corresponding key in your key ring.
The ```--armor"``` option will save the data in text format (binary data will be represented by displayable ASCII characters).
Save the files with the keys in the password manager (use the option to attach files), as well as the revocation certificate (the path to it was displayed in the terminal after creating the key pairs).
The revocation certificate is used if the private key has been compromised and must be kept separate from the private key. Later, you can pick out the revocation certificate from the password manager and save it in another safe place, or delete it now and generate a new one later.
After saving in the password manager, delete the files with the secret key and the revocation certificate from the disk in a safe way - using the [Eraser][eraser] app.
The secret key is stored on the disk in an encrypted form, i.e. it requires a password to use it, but still it is recommended to delete it securely.

:writing_hand: A self-study task (performed in pairs): perform an encrypted transmission of the message:
1) Add the partner's public key to your keyring.
2) Create a file with a short text message.
3) Encrypt it with GnuPG using the partner's public key.
4) Send a message to a partner, ask him to decipher and voice it to you.

## <a name=online-repos /> 6. Online repositories

The most popular repository management services today are [GitHub], [GitLab] and [BitBucket].

- Get yourself an account on GitHub (use the first email address intended for registrations).
- Enter the credentials in the password manager.
- Add your public key in your profile settings.
- Add an email address (the second one that is for public usage) and verify it.
- Generate a cryptographic "token" - check the box that allows you to manage repositories.
- Enter the token in the password manager: enter your login in the name field, insert the token in the password field.

Create a test repository, check the box "create readme.md file".
Go to the settings of the repository, in the "pages" tab activate web page hosting.
 
## <a name=git /> 7. Version control

Download and install [git].

Go to the path ```C:\Program Files\Git\usr\bin\```.
Rename the file "gpg.exe" to, for example, "gpg-in-git.exe". It is recommended to do the same with the rest of the files in this folder that are related to the GnuPG program.
This will make the version of [GnuPG][gpg] you installed earlier available from the Bash terminal instead of the version of GnuPG that comes with Git.

### Initial Git setup
#### System settings
Disable credential helper (caching entered passwords):  
```git config --unset --system credential.helper```    
Disabling the interactive window for entering credentials (so that the input is from the terminal):   
```git config --system core.askPass ""```

#### Global settings
Set the text editor to launch when editing messages:  
```git config --global core.editor notepad```  
Set the location of the GnuPG program:  
```git config --global gpg.program gpg```

Enter information about yourself (must match the information in your gpg key):     
```git config --global user.name "Name Surname"```  
```git config --global user.email your_email@address.com```  

Activate options to digitally sign commits and tags:  
```git config --global commit.gpgsign true```  
```git config --global tag.gpgsign true```  

Set the key ID that Git will use to sign commits and tags:  
```git config --global user.signingkey <keyID>```  

View settings:  
```git config --list --show-origin```  

#### Creating a repository

Create a new folder:  
```mkdir test```  
Initialize a new repository in it:  
```git init```  
Link it to the GitHub repository:    
```git remote add origin https://github.com/<your_login>/test.git```  

Make an empty root commit:  
```git commit --allow-empty -m "Empty root"```  
Anchor a tag to it:  
```git tag root -m "Start point"```  
Create an ignore list file:  
```notepad .gitignore```  
Create or paste a new file with a simple web page:  
```notepad index.html```  
Добавим все файлы в репозиторий:   
```git add --all```  
Check the status:  
```git status```  
Make a commit:  
```git commit```  
View the commit tree:  
```git log --graph --all --show-signatures```  
Upload the repository to Github, take the username and token from the password manager:  
```git push origin main --tags -f```  
*The ```-f``` option here allows overwriting the repository completely, it is not recommended to use it in the future, as it changes the commit history (read the details in the official documentation).*
Check the commit tree again:  
```git log --graph --all --show-signatures```  

If you did everything right, then after a short period of time the page will become available online:  
```https://<your_login>.github.io/test/```  

## <a name=hometask /> Home task
The hometask is here: [hometask].  
***Don't miss the epic fight of overminds!***  
[![Banner][banner]][hometask]

## <a name=part2 /> Part II :deciduous_tree: - your ecosystem

# UNDER CONSTRUCTION, COME BACK SOON!

### <a name=ide /> Installation of an integrated development system

### <a name=syntax-highlight /> Syntax highlight

### <a name=intelli-sense /> Smart completion

### <a name=extensions /> Extensions

### <a name=static-analysis /> Static code analysis

### <a name=debug /> Debugging (dynamic code analysis)

### <a name=terminal /> Built-in terminal

### <a name=version-control /> Built-in version control system

### <a name=live-server /> Live server

### <a name=exercise /> Exercise for independent work


## <a name=author-contacts /> Author and contacts

***Alexander Nord***, aka ***"Dr. Nord"*** - Doctor of Engineering Sciences, Professor:
- scientific research and academic supervising;
- training individually and in groups;
- design and development;
- preparation of training courses (general, specialized, individual).  
*Through thorns to stars!*

:e-mail: <nordexium@gmail.com> - **write** a letter or...  
:octocat: https://drnord.github.io - **explore** other Dr. Nord's resources and **use** alternative means of **communication**.

[README.md]: README.md
[README-RU.md]: README-RU.md
[lesson-p1]: https://youtu.be/rM7al2ZmHxQ
[lesson-p2]: https://youtube.com

[LICENSE-DN.txt]: LICENSE-DN.txt
[cefr]: https://tracktest.eu/english-levels-cefr/

[ddgo]: https://duckduckgo.com
[google]: https://google.com

[mdn]: https://developer.mozilla.org/
[KeePass]: https://keepass.info/
[eraser]: https://eraser.heidi.ie/
[gpg]: https://www.gnupg.org/
[GitHub]: https://github.com/
[GitLab]: https://gitlab.com/
[BitBucket]: https://bitbucket.org/
[git]: https://git-scm.com/

[hometask]: https://drnord.github.io/IT-startright/index-ru.html
[banner]: ./img/spider-mastermind.png

[VS-code]: https://code.visualstudio.com/
[firefox-inst]: https://www.mozilla.org/en-US/firefox/all/#product-desktop-release/
[firefox-external-control]: https://github.com/firefox-devtools/vscode-firefox-debug/
[gpg-key]: https://github.com/spider-mastermind-dis/gpg-key/
