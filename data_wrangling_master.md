# Data Wrangling (数据整理) — Master Guide

---

## Introduction

**Data wrangling** is the process of transforming and cleaning raw data into a format that is easier to analyze, visualize, or use for further processing. It is a foundational skill for anyone working with data, whether text or binary, local or remote.

---

## Mind Map Structure

Data wrangling can be broken down into the following main areas:

- **Basic Techniques**
- **Use Cases**
- **Tools**
- **Data Analysis**
- **Binary Data**
- **Determining Parameters**

---

## 1. Basic Techniques

- **Filtering:** Select relevant data (e.g., `grep`, `awk`).
- **Sorting:** Arrange data (`sort`).
- **Grouping & Counting:** Aggregate and summarize (`uniq -c`, `awk`).
- **Extracting Fields:** Isolate columns/values (`cut`, `awk`).
- **Substitution & Editing:** Modify data (`sed`).

---

## 2. Use Cases

- **Log Analysis:** Extracting info from logs.
- **Data Cleaning:** Removing duplicates, fixing formats.
- **Data Transformation:** Converting between formats (CSV, JSON, etc.).
- **Batch Processing:** Automating repetitive tasks.
- **Remote Data Processing:** Using SSH and pipelines on remote servers.

---

## 3. Tools

- **grep:** Pattern-based filtering
- **awk:** Field extraction, filtering, reporting
- **sed:** Stream editing and substitution
- **sort/uniq:** Sorting and deduplication
- **cut/paste:** Column extraction and merging
- **xargs:** Building command arguments from data
- **bc:** Command-line calculator
- **R/gnuplot:** Statistical analysis and visualization
- **ffmpeg/convert/gzip:** Binary and image data processing

---

## 4. Data Analysis

- **Statistical Summaries:** `awk`, `R`, `bc`
- **Visualization:** `gnuplot`, `R`
- **Pattern Recognition:** Spotting trends/anomalies

---

## 5. Binary Data

- **Image/Video Processing:** `ffmpeg`, `convert`
- **Compression:** `gzip`, `bzip2`
- **Pipelines:** Chaining tools for binary data

---

## 6. Determining Parameters

- **Dynamic Arguments:** Generating command-line arguments (`xargs`)
- **Automated Workflows:** Using wrangled data for automation
- **Integration:** Feeding processed data into other scripts/tools

---

## Key Concepts & The Pipe Operator

- The **pipe (`|`)** connects commands, sending output from one as input to the next.
- Example:
  ```bash
  journalctl | grep -i intel
  ```
- Regular expressions (regex) are used for powerful pattern matching in tools like `grep`, `sed`, and `awk`.
- Data wrangling is about combining simple tools to solve complex problems.

---

## Practical Command-Line Examples

### 1. Filter Log Entries by Date
```bash
grep "May 10" /var/log/syslog
```
*Shows only lines containing "May 10" in the syslog file.*

---

### 2. Find the Top 5 Most Common IP Addresses in a Log
```bash
awk '{print $1}' access.log | sort | uniq -c | sort -nr | head -5
```
*Extracts the first field (IP), counts occurrences, sorts by count, and shows the top 5.*

---

### 3. Extract Email Addresses from a File
```bash
grep -E -o "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" file.txt | sort | uniq
```
*Finds and lists unique email addresses in a file.*

---

### 4. Replace All Tabs with Commas in a File
```bash
sed 's/\t/,/g' data.tsv > data.csv
```
*Replaces all tabs with commas and saves as a new file.*

---

### 5. Show Only Lines 10 to 20 of a File
```bash
sed -n '10,20p' file.txt
```
*Prints lines 10 through 20.*

---

### 6. Calculate the Average of Numbers in a File
```bash
awk '{sum+=$1} END {print sum/NR}' numbers.txt
```
*Sums all numbers and divides by the number of lines.*

---

### 7. Combine Two Columns from Two Files Side by Side
```bash
paste file1.txt file2.txt
```
*Shows columns from both files side by side.*

---

### 8. Remove Duplicate Lines from a File
```bash
sort file.txt | uniq
```
*Sorts and removes duplicate lines.*

---

### 9. Count the Number of Files by Extension in a Directory
```bash
ls | awk -F. '{print $NF}' | sort | uniq -c
```
*Counts files by their extension.*

---

### 10. Find and Replace Text in Multiple Files
```bash
sed -i '' 's/foo/bar/g' *.txt
```
*(On macOS; use `-i` without quotes on Linux.)*

---

### 11. Get the Last 100 Lines of a Growing Log File (Live)
```bash
tail -f -n 100 /var/log/syslog
```
*Shows the last 100 lines and updates as new lines are added.*

---

### 12. Extract the Second Column from a CSV File
```bash
cut -d, -f2 data.csv
```
*Prints the second column.*

---

### 13. Find All Unique Words in a Text
```bash
tr -cs '[:alnum:]' '[\n*]' < file.txt | sort | uniq
```
*Splits text into words, sorts, and removes duplicates.*

---

### 14. Count the Number of Lines, Words, and Characters in a File
```bash
wc file.txt
```
*Shows line, word, and character counts.*

---

### 15. Chain Multiple Tools for Complex Tasks
```bash
grep "error" app.log | sort | uniq -c | sort -nr | head -3
```
*Filters for "error", counts unique messages, sorts by frequency, and shows the top 3.*

---

## Key Takeaways

- Data wrangling is about transforming data through a series of steps.
- The pipe (`|`) is fundamental to chaining commands.
- Regular expressions are powerful but require careful use.
- Tools like `sed`, `awk`, and `grep` are essential for text processing.
- Data wrangling works for both text and binary data.
- Understanding your tools and how to combine them is crucial.
- Remote data processing can be more efficient than local processing.
- Always consider bandwidth and processing efficiency when working with large datasets.
- Each tool has its strengths—choose the right tool for the job.
- Complex transformations can be achieved by combining simple tools.

--- 