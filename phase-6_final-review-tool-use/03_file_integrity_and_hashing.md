# 03 — File Integrity & Hashing Tools

---

## Scenario

This module focused on verifying file integrity and detecting tampering using cryptographic hashes. These tools are essential for identifying unauthorized changes to sensitive files, spotting malware droppers, and confirming system integrity during incident response. I simulated real-world tamper detection using tools like `sha256sum`, `diff`, and `find`.

---

## What I Did

```bash
# Created a baseline hash for a known-good file
sha256sum /etc/passwd > baseline.hash

# Simulated file tampering
cp /etc/passwd ./fakepasswd
echo "# Backdoor user" >> fakepasswd

# Verified change using hash and diff
sha256sum fakepasswd
diff /etc/passwd fakepasswd
sha256sum -c baseline.hash

# Tested alternative hashing algorithms
md5sum fakepasswd
sha1sum fakepasswd

# Investigated recent changes in critical directories
find /etc -type f -mtime -1

# Searched for unexpected binaries in /tmp
find /tmp -type f -executable
```

---

## What I Learned

- File hashes like SHA256 provide a cryptographic fingerprint that can quickly prove if a file has been altered.
- Comparing original and modified files using `diff` and hash mismatch is a reliable method for tamper detection.
- System directories like `/etc` should rarely change — tools like `find -mtime` can identify unauthorized modifications.
- Threat actors often drop binaries into `tmp`, `shm`, or user-writable directories to bypass detection.

---

## Why It Matters

File integrity monitoring is foundational to intrusion detection. Whether it’s verifying that system binaries haven’t been replaced or spotting backdoored configs, knowing how to generate and validate file hashes helps confirm or disprove compromise. These tools also reinforce digital forensics and root cause analysis skills.

---

