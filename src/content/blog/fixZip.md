---
title: "crack zip password"
description: ""
pubDate: "July 31 2023"
heroImage: ""
badge: "zip"
---

In 2021, bulk of images were archived into zip password protected files using the "Es file manager" on the phone and backed up via Telegram. A year later, I tried to access but forgot what was a password set on the zip. I was little familiar with linux bash shell and on **kali linux** used **zip2john** tool to crack but failed, saying something like file *corrupted* by time gap attempted sometimes, same problem 😂🤣 . Today, I found a tool called [fcrack](https://www.kali.org/tools/fcrackzip/) 

```bash
fcrackzip -v -u -D -p /usr/share/wordlists/rockyou.txt encrypted.zip
```

**oh..! wait zip file is still say**

```bash
'encrypted/IMG_20210917_214858.jpg' is corrupted, skipping zipfile no usable files found
```

Then i copy paste error on poe.com it suggest [response-link](https://poe.com/s/tVOsv7lYIOXo4UBAQ6Q6)

```
The error message you received indicates that the file 'IMG_20210917_214858.jpg' within the ZIP file is corrupted and cannot be opened. As a result, the entire ZIP file cannot be extracted.
There are a few possible reasons why the file may be corrupted, such as an incomplete download or a problem with the original file. You could try re-downloading the ZIP file again to see if that resolves the issue.
Alternatively, you could try using a ZIP repair tool to fix the corrupted file within the ZIP file. One such tool is called "Zip Repair Pro". You can download and install this tool on your system, and then use it to repair the corrupted file within the ZIP file.
If neither of these options work, you may need to contact the owner of the ZIP file to obtain a new, uncorrupted version of the file.
```

Search on google `how can i fix corrupt zip file in kali linux` found this https://superuser.com/questions/23290/terminal-tool-linux-for-repair-corrupted-zip-files
use this command to fix zip error

```bash
zip -FF Corrupted.zip --out New.zip
```
Again use first command boom its shows password.