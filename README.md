# Linux Compression Practice

This project contains hands-on practice of Linux compression tools using `gzip` and `xz`, focusing on:

- Creating and compressing large files
- Using different compression levels
- Understanding the effect of each level
- Reading compressed files without decompressing
- Observing behavior during decompression

---

## 📁 Folder Structure

linux-compression-practice/
├── bigfile # Original file
├── compressed/ # All compressed files
├── commands.txt # All commands used
└── README.md # This documentation file

---
```bash
cat /etc/* > bigfile 2> /dev/null
### 🔹 Gzip with compression level 1 and 9:
cp bigfile compressed/bigfile-gz1
cp bigfile compressed/bigfile-gz9
gzip -1 compressed/bigfile-gz1
gzip -9 compressed/bigfile-gz9

### 🔹 xz with compression level 1 and 9:
cp bigfile compressed/bigfile-xz1
cp bigfile compressed/bigfile-xz9
xz -1 compressed/bigfile-xz1
xz -9 compressed/bigfile-xz9
### 🔹 Decompress and observe behavior:
gunzip compressed/bigfile-gz1.gz
### 🔹 Read compressed files without decompressing:
cp /etc/hosts ./compressed/
gzip ./compressed/hosts
zcat ./compressed/hosts.gz

###  What I Learned

- Compression levels (`-1` to `-9`) impact speed and file size.
- `gzip` is faster, `xz` gives smaller files.
- Compressed files are deleted automatically after decompression unless you use `-k`.
- Tools like `zcat`, `zgrep`, `zless` help read `.gz` files directly.
