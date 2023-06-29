---
title: "Mount iPhone on your linux machince"
description: "Mount  directories of an iOS device locally using fuse. By default the media directory is mounted, options allow to also mount the sandbox container of an app, an app's documents folder or even the
       root filesystem on jailbroken devices."
pubDate: "June 26 2023"
heroImage: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSwus5NOJT6b3oTevs05R_Up4uMvh1cfy48pA&usqp=CAU"
badge: "iPhone"
---
## ifuse basic command

### unmount your iphone when you have mount

```bash
fusermount -u ~/iPhone
```

### mount documents in iPhone directory

```bash
ifuse --documents com.spotify.client ~/iPhone
```

### view that share file in yor iPhone

```bash
ifuse --list-apps
```

### if want mount all your iPhone directory

```bash
ifuse ~/iPhone/
```

##### Oh i forget to mention your should make iPhone folder on home folder, simply copy paste above code. 

```bash
mkdir iPhone
```
