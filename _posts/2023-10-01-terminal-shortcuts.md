---
title: Essential Terminal Shortcuts
date: 2023-10-01 -0300
categories: [Tutorials, Linux]
tags: [linux-terminal, linux]
mermaid: true
---

If you are a Linux user,and you also like to use the terminal, this terminal shortcuts will be very useful for your daily tasks.

## Ctrl + A (Move to the start of the line)

When you press the `Ctrl + a`, it will shift the cursor to the beginning of the line, which can be really helpful when you write a long command and want to make changes at the beginning of the line.

### Ctrl + E (Move to the end of the line)

When you press the `Ctrl + e`, it will shift the cursor to the end of the line.

### Ctrl + U (Delete from the cursor to the start of the line)

Sometimes, you want to remove everything from the cursor position to the beginning of the line (everything from the cursor position to the left-hand side). With the command `Ctrl + u`, you can do this job.

### Ctrl + K (Delete from the cursor to the end of the line)

Contrary to the previous command, `Ctrl + k` remove everything from the cursor position to the end of the line.

### Ctrl + W (Delete the word before the cursor)

The two commands above remove everything from the cursor position to the beginning (left) or end (right) of the line. This command `Ctrl + w` remove a single word before the cursor.

### Ctrl + D (Log out or exit the terminal)

My favorite shortcut. When you want to log out of the terminal, you have a few options; you can use the Windows terminal button, or use the `exit` command. The shortcut `Ctrl + d` allows you to do this without typing anything, just press these two keys and log out in a faster way. If you use it in SSH, it will close the session, and if pressed again, it will close the terminal itself.

### Ctrl + C (Stop the current process/command)

Many times, you need to stop the execution of a command, and you don't know how to do it. Most of the time, people end up closing the terminal itself. When you press `Ctrl + c`, it sends the `SIGINT` signal that will kill the process.

### Ctrl + Z (Pause the current process (can be resumed))

In the above command, you can see how to stop a process, but sometimes, you have to resume this process, and killing it is not a good idea. So, in that case, what you can do is press `Ctrl + z` to stop the ongoing process and then continue from where you left off.

There is no keyboard shortcut to resume a suspended process. To resume the process, you'd have to use the `-CONT` flag with the `kill` command as shown:

```sh
kill -CONT <PID>
```
{: .nolineno }

You can see the PID in the output when the process is suspended. In this case is `433633`.

```sh
433633 suspended  sudo dnf upgrade
```

### Ctrl + R (Search command history (backward search))

`Ctrl + r` is the shortcut that opens a search mode in the prompt, where you can type any part of the command, and it will find you the command that matches the string you've entered.
