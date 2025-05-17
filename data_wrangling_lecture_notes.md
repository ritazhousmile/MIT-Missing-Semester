# Data Wrangling Lecture Notes

## Introduction to Data Wrangling

Data wrangling is the process of transforming data from one format to another until you achieve your desired result. This lecture focuses on massaging data, whether in text or binary format, to get exactly what you want.

### Basic Data Wrangling with Pipes

The pipe operator (`|`) is fundamental to data wrangling. For example:
```bash
journalctl | grep -i intel
```
This command transforms system logs into filtered Intel-related entries. Data wrangling is about knowing your tools and how to combine them effectively.

## Practical Example: Server Log Analysis

### Step 1: Accessing Remote Logs
```bash
ssh myserver journalctl
```

### Step 2: Filtering SSH Logs
```bash
ssh myserver journalctl | grep sshd
```
Note: We're using a pipe to stream remote files through local `grep`!

### Step 3: Further Filtering
```bash
ssh myserver 'journalctl | grep sshd | grep "Disconnected from"' | less
```
The additional quoting is important because:
- Logs can be large
- Filtering on the remote server saves bandwidth
- `less` provides a pager for scrolling through output

### Step 4: Saving Filtered Logs
```bash
ssh myserver 'journalctl | grep sshd | grep "Disconnected from"' > ssh.log
less ssh.log
```

## Using `sed` for Text Processing

`sed` (stream editor) is a powerful tool for modifying text streams. It's based on the old `ed` editor and uses short commands for modifications.

### Basic Substitution
```bash
sed 's/.*Disconnected from //'
```
- `s` command format: `s/REGEX/SUBSTITUTION/`
- Similar to Vim's search and replace syntax

### Regular Expressions in `sed`

Common patterns:
- `.` : Any single character (except newline)
- `*` : Zero or more of preceding match
- `+` : One or more of preceding match
- `[abc]` : Any one character of a, b, and c
- `(RX1|RX2)` : Either RX1 or RX2
- `^` : Start of line
- `$` : End of line

Note: In `sed`, you often need `\` before special characters, or use `-E` flag.

### Advanced Pattern Matching
```bash
sed -E 's/.*Disconnected from (invalid |authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/'
```
- Uses capture groups (parentheses)
- `\1`, `\2`, etc. refer to captured groups
- Handles complex patterns like usernames with spaces

## Data Analysis Pipeline

### Finding Common Usernames
```bash
ssh myserver journalctl
 | grep sshd
 | grep "Disconnected from"
 | sed -E 's/.*Disconnected from (invalid |authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/'
 | sort | uniq -c
 | sort -nk1,1 | tail -n10
```
- `sort` : Orders input
- `uniq -c` : Collapses identical lines with count
- `sort -n` : Numeric sort
- `-k1,1` : Sort by first column
- `tail -n10` : Get top 10 results

### Creating Comma-Separated List
```bash
# ... previous pipeline ...
 | awk '{print $2}' | paste -sd,
```
Note: On macOS, you might need GNU coreutils for `paste`

## Introduction to `awk`

`awk` is a programming language excellent for processing text streams.

### Basic Usage
```bash
awk '{print $2}'  # Print second field of each line
```
- `$0` : Entire line
- `$1` through `$n` : nth field
- Default field separator is whitespace

### Advanced `awk` Example
```bash
awk '$1 == 1 && $2 ~ /^c[^ ]*e$/ { print $2 }' | wc -l
```
- Pattern matching
- Regular expressions
- Field comparison

### Full `awk` Program
```awk
BEGIN { rows = 0 }
$1 == 1 && $2 ~ /^c[^ ]*e$/ { rows += $1 }
END { print rows }
```
- `BEGIN` : Matches start of input
- `END` : Matches end of input
- Can replace multiple tools in pipeline

## Data Analysis Tools

### Basic Math with `bc`
```bash
paste -sd+ | bc -l  # Add numbers
echo "2*($(data | paste -sd+))" | bc -l  # More complex expressions
```

### Statistical Analysis with R
```bash
# ... previous pipeline ...
 | awk '{print $1}' | R --no-echo -e 'x <- scan(file="stdin", quiet=TRUE); summary(x)'
```

### Plotting with `gnuplot`
```bash
# ... previous pipeline ...
 | gnuplot -p -e 'set boxwidth 0.5; plot "-" using 1:xtic(2) with boxes'
```

## Advanced Applications

### Using `xargs` for Command Arguments
```bash
rustup toolchain list | grep nightly | grep -vE "nightly-x86" | sed 's/-x86.*//' | xargs rustup toolchain uninstall
```

### Binary Data Wrangling
Example pipeline for image processing:
```bash
ffmpeg -loglevel panic -i /dev/video0 -frames 1 -f image2 -
 | convert - -colorspace gray -
 | gzip
 | ssh mymachine 'gzip -d | tee copy.jpg | env DISPLAY=:0 feh -'
```
Tools used:
- `ffmpeg` : Video/image capture
- `convert` : Image transformation
- `gzip` : Compression
- `ssh` : Remote transfer
- `tee` : Split output
- `feh` : Image display

## Key Takeaways

1. Data wrangling is about transforming data through a series of steps
2. The pipe operator (`|`) is fundamental to chaining commands
3. Regular expressions are powerful but require careful use
4. Tools like `sed`, `awk`, and `grep` are essential for text processing
5. Data wrangling works for both text and binary data
6. Understanding your tools and how to combine them is crucial
7. Remote data processing can be more efficient than local processing
8. Always consider bandwidth and processing efficiency when working with large datasets 