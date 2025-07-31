---
title: 'Packer OVA'
date: 2016-04-23
lastmod: 2016-04-23

# Keywords help in classifying content
keywords:
  - Packer OVA
  - Packer
  - OVA
  - How To
---

Recently I have started using [Packer](https://www.packer.io/) to build AMI images. It works like a champ, but then I tried to make VMWare images and it produced machine images, not machine exports. This makes the exports nearly useless. However, with a little post-processing magic this can be fixed.

<!--more-->

There is a GoLang based [ovftool post processor](https://github.com/iancmcc/packer-post-processor-ovftool) that already does this, but it needs to be compiled and put into the packer plugins dir. Nothing that the plugin does requires GoLang, so I whipped up a quick bash version that I could include with the packer script.

VMWare comes bundled with a tool called `ovftool` which will convert a machine image into a OVA file. It has a lot of useful options so I recommend you reading the manual page. Basically it take a `vmx` file and its associated files and makes a OVA: `ovftool sourc.vmx dest.ova`.

I turned this into a script that can be called as a post processor from packer. There are a number of protections, but the important items are:

1. line 5: Ensures `ovftool` is on the path
2. line 19: This avoids an interesting behavior (read bug) of Packer where the the inline script is called multiple times; once per file in the output directory.
3. line 33: Removes the floppy which is used to install some VMWare drivers.
4. line 37: Removes the CD-Room that is also used to install some VMWare drivers.
5. line 42: Uses `ovftool` to create an OVA.

```bash
#!/bin/bash

# Make sure ovftool is in the path.
# On the mac:
PATH=/Applications/VMware\\\\ Fusion.app/Contents/Library/VMware\\\\ OVF\\\\ Tool/:$PATH

# I need to be given the output path and vmname.
if [ -z "$1" -o -z "$2" ]; then
  echo "output path and vm-name are required"
  exit 1
fi

DIR=$1
NAME=$2

cd $DIR

# I may be called multiple times.  If so bail early
if [ -f "${NAME}.ova" ]; then
  echo "OVA already created, skipping"
  exit 0
fi

if [ ! -f "${NAME}.vmx" ]; then
  echo "no ${NAME}.vmx file found"
  exit 1
fi

# bail on error
set -e

# remove floppy
sed '/floppy0\\\\./d' ${NAME}.vmx > 1.tmp
echo 'floppy0.present = "FALSE"' >> 1.tmp

# remove CD
sed '/ide1:0\\\\.file/d' 1.tmp | sed '/ide1:0\\\\.present/d' > 2.tmp
echo 'ide1:0.present = "FALSE"' >> 2.tmp

mv 2.tmp ${NAME}.vmx

ovftool -dm=thin --compress=1 ${NAME}.vmx ${NAME}.ova
```

Add this script to the packer JSON files.

```json
{
    "variables": {
        "output_path": "output",
        "vm_name": "data-collector",
        ...
    },

    "builders": [{
        "output_directory": "{{ user `output_path` }}",
        "vm_name": "{{ user `vm_name` }}",
        ...
    }],

    "_comment": "Create an OVA because packer cannot.",
    "post-processors": [{
        "type": "shell-local",
        "inline": ["post-ova.sh {{user `output_path`}} {{user `vm_name`}}"]
    }]
}
```
