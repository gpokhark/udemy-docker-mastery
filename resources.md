# Section 1
## 4. Getting Course Resources (GitHub Repo)
- GitHub repo - https://github.com/bretfisher/udemy-docker-mastery
- [Cheat Sheet](./resources/Docker_CheatSheet_08.09.2016_0.pdf)
- PPT
- [Commands](./resources\Docker+Mastery+Commands+2.0/) 
# Section 2
## 11. Docker for Windows 10: Setup and Tips
- [Tab Completion](https://github.com/matt9ucci/DockerCompletion)
- [Docker Desktop for Windows user manual](https://docs.docker.com/docker-for-windows/)
## 12. Docker for Mac Setup and Tips
## 13. Docker for Linux Setup and Tips
- [Install Docker Compose](https://docs.docker.com/compose/install/)
- [Install Docker Machine](https://docs.docker.com/machine/install-machine/)
# Section 3
## 21. Container VS. VM: It's Just a Process
- [Docker PDF ebook](https://github.com/mikegcoleman/docker101/blob/master/Docker_eBook_Jan_2017.pdf)
- [Cgroups, namespaces, and beyond: what are containers made from?](https://www.youtube.com/watch?list=PLBmVKD7o3L8v7Kl_XXh3KaJl9Qw2lyuFl&v=sK5i-N34im8&feature=youtu.be&ab_channel=Docker)
- [Docker Desktop for Mac Commands for Getting Into The Local Docker VM](https://www.bretfisher.com/docker-for-mac-commands-for-getting-into-local-docker-vm/)
- [Getting a Shell in the Docker for Windows Moby VM](https://www.bretfisher.com/getting-a-shell-in-the-docker-for-windows-vm/)
## 22. Windows Containers: Docker Is No Longer Just Linux
- [Windows Containers and Docker: 101](https://www.youtube.com/watch?v=066-9yw8-7c&ab_channel=Docker)
- [Beyond \ - the path to Windows and Linux parity in Docker](https://www.youtube.com/watch?v=4ZY_4OeyJsw&ab_channel=Docker)
- [Docker + Microsoft - Investing in the Future of your Applications](https://www.youtube.com/watch?v=QASAqcuuzgI&ab_channel=Docker)
## 26. Getting a Shell Inside Containers: No Need for SSH
- [Package Management Basics: apt, yum, dnf, pkg](https://www.digitalocean.com/community/tutorials/package-management-basics-apt-yum-dnf-pkg)
## 27. Docker Networks: Concepts for Private and Public Comms in Containers
- [Format command and log output](https://docs.docker.com/config/formatting/)
## 30. Docker Networks: DNS and How Containers Find Each Other
- [How DNS Works](https://howdns.works/)
- [Oracle Buys Dyn](https://www.oracle.com/corporate/acquisitions/dyn/)
## 34. Assignment: DNS Round Robin Test
- [Round-robin DNS](https://en.wikipedia.org/wiki/Round-robin_DNS)
# Section 4
## 36. What's In An Image (and What Isn't)
- [Docker Image Specification v1.0.0](https://github.com/moby/moby/blob/master/image/spec/v1.md)
## 37. The Mighty Hub: Using Docker Hub Registry Images
- [docker-library/official-images/](https://github.com/docker-library/official-images/tree/master/library)
## 38. Images and Their Layers: Discover the Image Cache
- [About storage drivers](https://docs.docker.com/storage/storagedriver/)
## 40. Building Images: The Dockerfile Basics
- [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)
# Section 5
## 46. Container Lifetime & Persistent Data
- [An introduction to immutable infrastructure](https://www.oreilly.com/radar/an-introduction-to-immutable-infrastructure/)
- [The Twelve Factor App](https://12factor.net/)
- [12 Fractured Apps](https://medium.com/@kelseyhightower/12-fractured-apps-1080c73d481c#.cjvkgw4b3)
- [Manage data in Docker](https://docs.docker.com/storage/)
## 48. Shell Differences for Path Expansion
In the next lecture, you'll learn how to share files and directories between a host and a Docker container. One of the parts of the command line you'll need to type is the host file path you want to share.

With Docker CLI, you can always use a full file path on any OS, but often you'll see me and others use a "parameter expansion" like `$(pwd)` which means "print working directory".

Here's the important part. Each shell may do this differently, so here's a cheat sheet for which OS and Shell your using. I'll be using $(pwd) on a Mac, but yours may be different!

This isn't a Docker thing, it's a Shell thing.

For PowerShell use: `${pwd}` 

For cmd.exe "Command Prompt use: `%cd%`

Linux/macOS bash, sh, zsh, and Windows Docker Toolbox Quickstart Terminal use: `$(pwd)` 

Note, if you have spaces in your path, you'll usually need to quote the whole path in the docker command.
## 52. Assignment: Edit Code Running In Containers With Bind Mounts
- [Transform your plain text into static websites and blogs.](https://jekyllrb.com/)
## 54. Database Passwords in Containers
We all know databases usually need passwords, but since the dawn of Docker, the postgres image (and a few others like redis) has allowed you to do a simple `docker run` on it and it starts without a password. Sure you could set a password but it didn't require one.

In Feburary 2020 that changed, and will affect using postgres in this course (and my others). When running postgres now, you'll need to either set a password, or tell it to allow any connection (which was the default before this change).

For `docker run`, and the forthcoming Docker Compose sections, you need to either set a password with the environment variable:

`POSTGRES_PASSWORD=mypasswd`

Or tell it to ignore passwords with the environment variable:

`POSTGRES_HOST_AUTH_METHOD=trust`

Note this change was in the Docker Hub image, and not a change in postgres itself.

Also note if I or you were pinning versions, as we should, this wouldn't have surprised us. I tend to only pin to the minor version in this course (9.6) rather than the patch version (9.6.16) to keep you a bit more secure in the course. In the real world, I always pin my production apps to the patch version. It's the only safe way to operate. By pinning to the minor version in the courses, I prevent any major changes from breaking the course (in theory ha ha), yet also ensure you're running the latest patches (which would fix any bugs or security problems). In this, *very rare case*, the maintainer of the official postgres decided to introduce a breaking change in the *image* to a patch release of the app. The two aren't related, and it kinda shows off a weakness of the Docker Hub model... that there is no version of the Docker Hub image really, it's just tracking the upstream postgres versions... so then if any Docker Hub change would break something, it can't easily be tracked as a separate version from the app itself. Oh well, just remember to always pin the whole image version for things you care about.

I've updated the course repo files to indicate this change, but if you've cloned the repo before February 18th, 2020, you will need to update or replace your clone.
# Section 6
## 55. Docker Compose and The docker-compose.yml File
- [The YAML Format: Sample Generic YAML file](https://yaml.org/start.html)
- [The YAML Format: Quick Reference](https://yaml.org/refcard.html)
- [Compose file versions and upgrading](https://docs.docker.com/compose/compose-file/compose-versioning/)
- [Docker Compose Release Downloads](https://github.com/docker/compose/releases)
## 56. Trying Out Basic Compose Commands
- [Only one host for production environment. What to use: docker-compose or single node swarm?](https://github.com/BretFisher/ama/issues/8)
## 57. Assignment: Build a Compose File For a Multi-Container Service
- [Compose file Reference](https://docs.docker.com/compose/compose-file/)
# Section 7
# Section 8
# Section 9
# Section 10
# Section 11
# Section 12
# Section 13
# Section 14
# Section 15
# Section 16
# Section 17
# Section 18
# Section 19
# Section 20
# Section 21
# Section 22
