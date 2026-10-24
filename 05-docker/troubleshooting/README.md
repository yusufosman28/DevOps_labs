# Troubleshooting: What Broke and How I Fixed It

![Practice](https://img.shields.io/badge/Practice-Troubleshooting-red)
![Containers](https://img.shields.io/badge/Containers-Docker-2496ED?logo=docker&logoColor=white)

Real build and runtime problems from my own Flask and MySQL project.

A pattern ran through most of them: the most visible message was not the real cause. Reading the output in order, and finding the first error, was the skill.

Each write-up covers the **problem**, how I **investigated** it, the **cause**, the **fix** and **what I learned**.

---

## Write-ups

1. [`mysqlclient` build failed](./01-mysqlclient-build-failed.md)  
   Finding a missing build tool in a long build log.

2. [Pull access denied](./02-pull-access-denied.md)  
   A second error caused entirely by the first.

3. [Compose file in the wrong folder](./03-compose-file-in-the-wrong-folder.md)  
   Blaming a warning instead of the real error.

4. [Size test gave identical results](./04-size-test-gave-identical-results.md)  
   Saving a file is not the same as rebuilding the image.

5. [Missing dots in build commands](./05-missing-dots-in-build-commands.md)  
   What `.` means to Docker.

A related Compose problem, a service name the app could not find, is written up under Networking: [Unknown Server Host](../../04-networking/troubleshooting/02-unknown-server-host.md).

⬅️ [Back to Docker](../)
