**Difference Between init and telinit Commands in Linux**

In traditional SysVinit-based Linux systems, two important commands are
used to manage **runlevels**:
` init `and` telinit `.

**Key Differences**

  ------------------------------------------------------------------------
  |**Feature** |  **init**                  |   **telinit**               |

  |:-------------|: ----------------------------:| -----------------------------:|
  |Main Role   |  Main process responsible for |Interface to send commands to
                booting and<br> managing         the` init `<br>process|
                runlevels (PID 1)            

  Execution   |  Executed directly by the   |  Used to communicate
                system or <br>administrator   with` init `during <br>system
                                             runtime|

  Common Usage | Used in system boot or   |   Used to change runlevel while
                manually (e.g.,` init3`)      the system is <br>running
                                             (e.g.,` telinit 5`)|

  Dependency |   Works independently    |    Depends on` init `(usually a
                                             symbolic link to<br>` init`)|
  ------------------------------------------------------------------------

**Checking the Link Between the Two**

You can verify that` telinit `is a symbolic link to` init `using the
following command:

```bash
ls -l /sbin/init /sbin/telinit
```
Example output:

```bash
lrwxrwxrwx 1 root root 4 Apr 1 /sbin/telinit -> init

-rwxr-xr-x 1 root root 123456 Apr 1 /sbin/init
```
![Annotation 2025-05-23 173855](./media/media/image1.png)


**Usage Examples**

- Switch to multi-user (text) runlevel:

```bash
sudo telinit 3
```
![Annotation 2025-05-23
174056](./media/media/image2.png)


- Switch to graphical runlevel:

```bash
sudo init 5
```
![Annotation 2025-05-23 174515](./media/media/image3.png)


- Check current and previous runlevel:

```bash
runlevel
```