---
title: "Change file/folder permission/ownership in Linux"
description: "change file and folder permission & ownership on linux file system by using `chown` && `chmod`, when you are have to access regularly on root directory"
pubDate: "June 19 2023"
heroImage: "https://linuxhint.com/wp-content/uploads/2021/06/change-directory-owner-Linux-11.png"
badge: "Linux"
---

## Change Directory Permission

How to change file/folder ownership?

```bash
sudo chown -R owner /
```

How to change file/folder permission like read/write/execute?

```bash
sudo chmod owner /
```

tips

- `-R` used for recursvely used for sub-directory
- owner like `root/$USER`
- / => your file location.
