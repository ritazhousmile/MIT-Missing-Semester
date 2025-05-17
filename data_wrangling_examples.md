# Data Wrangling: Practical Command-Line Examples

Here are practical, easy-to-understand data wrangling examples using command-line tools. Each example includes a short explanation and the command.

---

## 1. Filter Log Entries by Date

**Goal:** Show only log entries from May 10th.

```bash
grep "May 10" /var/log/syslog
```
*Shows only lines containing "May 10" in the syslog file.*

---

## 2. Find the Top 5 Most Common IP Addresses in a Log

**Goal:** See which IP addresses appear most often.

```bash
awk '{print $1}' access.log | sort | uniq -c | sort -nr | head -5
```
*Extracts the first field (IP), counts occurrences, sorts by count, and shows the top 5.*

---

## 3. Extract Email Addresses from a File

**Goal:** Pull out all email addresses.

```bash
grep -E -o "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" file.txt | sort | uniq
```
*Finds and lists unique email addresses in a file.*

---

## 4. Replace All Tabs with Commas in a File

**Goal:** Convert a tab-separated file to CSV.

```bash
sed 's/\t/,/g' data.tsv > data.csv
```
*Replaces all tabs with commas and saves as a new file.*

---

## 5. Show Only Lines 10 to 20 of a File

**Goal:** View a specific range of lines.

```bash
sed -n '10,20p' file.txt
```
*Prints lines 10 through 20.*

---

## 6. Calculate the Average of Numbers in a File

**Goal:** Find the average value from a list of numbers (one per line).

```bash
awk '{sum+=$1} END {print sum/NR}' numbers.txt
```
*Sums all numbers and divides by the number of lines.*

---

## 7. Combine Two Columns from Two Files Side by Side

**Goal:** Merge two files line by line.

```bash
paste file1.txt file2.txt
```
*Shows columns from both files side by side.*

---

## 8. Remove Duplicate Lines from a File

**Goal:** Keep only unique lines.

```bash
sort file.txt | uniq
```
*Sorts and removes duplicate lines.*

---

## 9. Count the Number of Files by Extension in a Directory

**Goal:** See how many `.txt`, `.csv`, etc. files you have.

```bash
ls | awk -F. '{print $NF}' | sort | uniq -c
```
*Counts files by their extension.*

---

## 10. Find and Replace Text in Multiple Files

**Goal:** Change "foo" to "bar" in all `.txt` files.

```bash
sed -i '' 's/foo/bar/g' *.txt
```
*(On macOS; use `-i` without quotes on Linux.)*

---

## 11. Get the Last 100 Lines of a Growing Log File (Live)

**Goal:** Watch new log entries as they happen.

```bash
tail -f -n 100 /var/log/syslog
```
*Shows the last 100 lines and updates as new lines are added.*

---

## 12. Extract the Second Column from a CSV File

**Goal:** Get just the second field from a comma-separated file.

```bash
cut -d, -f2 data.csv
```
*Prints the second column.*

---

## 13. Find All Unique Words in a Text

**Goal:** List every unique word.

```bash
tr -cs '[:alnum:]' '[\n*]' < file.txt | sort | uniq
```
*Splits text into words, sorts, and removes duplicates.*

---

## 14. Count the Number of Lines, Words, and Characters in a File

**Goal:** Get basic file statistics.

```bash
wc file.txt
```
*Shows line, word, and character counts.*

---

## 15. Chain Multiple Tools for Complex Tasks

**Goal:** Find the 3 most common error messages in a log.

```bash
grep "error" app.log | sort | uniq -c | sort -nr | head -3
```
*Filters for "error", counts unique messages, sorts by frequency, and shows the top 3.*

--- 