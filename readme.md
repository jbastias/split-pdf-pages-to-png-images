# split-pdf-pages-to-png-images

Use pdftk to split the pdf docs into pages then use sips to convert the pdf pages into png images. Use convert to compare images to see if they are 'the same'.

**use pdftk to split docs into indivual pages**

```
# usage
pdftk <file.pdf> burst
```

e.g.

```
$ pdftk fonts-Robo-d2AEaiMa4N.pdf burst
$ ls -l pg_*.pdf
-rw-r--r--  1 jbastias  staff   19434 Jan 14 17:23 pg_0001.pdf
-rw-r--r--  1 jbastias  staff  978222 Jan 14 17:23 pg_0002.pdf
-rw-r--r--  1 jbastias  staff  217468 Jan 14 17:23 pg_0003.pdf
-rw-r--r--  1 jbastias  staff  173002 Jan 14 17:23 pg_0004.pdf
-rw-r--r--  1 jbastias  staff  161125 Jan 14 17:23 pg_0005.pdf
-rw-r--r--  1 jbastias  staff  178523 Jan 14 17:23 pg_0006.pdf
-rw-r--r--  1 jbastias  staff   31838 Jan 14 17:23 pg_0007.pdf
```

**use sips to pdf into png image**

```
# usage
sips -s format png file.pdf --out file.png
```

e.g.

```
$ sips -s format png pg_0003.pdf --out pg_0003.png
/Users/jbastias/Desktop/test-analysis/pg_0003.pdf
/Users/jbastias/Desktop/test-analysis/pg_0003.png
```

**use imagemagick compare for png image comparisions**

```
# usage
compare -metric MAE <file1.png> <file2.png> null: 2>&1
```

e.g.
```
$ compare -metric MAE slide_002.png slide_002.png null: 2>&1
0 (0)%
```

