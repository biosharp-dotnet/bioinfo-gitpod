# Custom cheatsheets (tldr pages)

### Problem

If you search for a tldr cheatsheet for `fastqc` you'll notice that it doesn't exist

```
tldr multiqc
```

The following message will be shown

```
Warning: Page `multiqc` not found in cache.
Try updating with `tldr --update`, or submit a pull request to:
https://github.com/tldr-pages/tldr
```

### Solution


Fortunately, `tealdeer` (tldr) allows us to create our own cheatsheets on the CLI

https://dbrgn.github.io/tealdeer/usage_custom_pages.html

### 1. First we need to create a specific folder

`tldr` tool looks into this folder, _in addition_ to the default pages.

```
mkdir -p ~/.local/share/tealdeer/pages 
```

### 2. Create a file called `fastqc.page` in  `~/.local/share/tealdeer/pages`  and add the following content
```

```markdown
# FastQC

- Run FastQC in current directory

    fastqc ./

- Check FastQC version

   fastqc --version
```

### 3. Use the custom `tldr` page for `fastqc`

```
tldr fastqc
```
