mkdir -p linux-compression-practice/compressed
cd linux-compression-practice

# Create empty commands.txt
touch commands.txt

# Create README.md with content
cat << 'EOF' > README.md
# Linux Compression Practice

This project contains hands-on practice of Linux compression tools using \`gzip\` and \`xz\`, focusing on:

- Creating and compressing large files
- Using different compression levels
- Understanding the effect of each level
- Reading compressed files without decompressing
- Observing behavior during decompression

---

## 📁 Folder Structure

\`\`\`
linux-compression-practice/
├── bigfile                 # Original file
├── compressed/             # All compressed files
├── commands.txt            # All commands used
└── README.md               # This documentation file
\`\`\`

---

##  Exercises & Commands

### 🔹 Create a big file:

\`\`\`bash
cat /etc/* > bigfile 2> /dev/null
\`\`\`

### 🔹 Gzip with compression level 1 and 9:

\`\`\`bash
cp bigfile compressed/bigfile-gz1
cp bigfile compressed/bigfile-gz9
gzip -1 compressed/bigfile-gz1
gzip -9 compressed/bigfile-gz9
\`\`\`

### 🔹 xz with compression level 1 and 9:

\`\`\`bash
cp bigfile compressed/bigfile-xz1
cp bigfile compressed/bigfile-xz9
xz -1 compressed/bigfile-xz1
xz -9 compressed/bigfile-xz9
\`\`\`

### 🔹 Decompress and observe behavior:

\`\`\`bash
gunzip compressed/bigfile-gz1.gz
\`\`\`

> \`bigfile-gz1.gz\` is deleted automatically after decompression.

---

### 🔹 Read compressed files without decompressing:

\`\`\`bash
cp /etc/hosts ./compressed/
gzip ./compressed/hosts
zcat ./compressed/hosts.gz
\`\`\`

---

##  What I Learned

- Compression levels (-1 to -9) impact speed and file size.
- \`gzip\` is faster, \`xz\` gives smaller files.
- Compressed files are deleted automatically after decompression unless you use \`-k\`.
- Tools like \`zcat\`, \`zgrep\`, \`zless\` help read \`.gz\` files directly.
EOF

# Optional: Git init and commit if needed
if [ ! -d .git ]; then
  git init
fi
git add .
git commit -m "Initial commit: Linux compression practice setup"

