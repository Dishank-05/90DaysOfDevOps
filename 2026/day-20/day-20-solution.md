# Day 20 – Log Analyzer and Report Generator

## Task 1: Input and Validation

```bash
#!/bin/bash

set -euo pipefail

if [ $# -eq 0 ]; then
        echo "Provide Path to Log File"
        exit 1
fi

log_file=$1

if [ ! -f "$log_file" ]; then
        echo "Logfile doesn't exist"
        exit 1
fi

```

## Task 2: Error Count

```bash
error_count=$(grep -Ei "ERROR|Failed" "$log_file" | wc -l)
echo "Total Error Counts: $error_count"

```

## Task 3: Critical Events

```bash
critical_events=$(grep -ni "CRITICAL" "$log_file")
if [ -z "$critical_events" ]; then
        echo "No Critical events found"
else
        echo "$critical_events"
        echo ""

```
## Task 4: Top Error Messages

```bash
echo "--- Top 5 Error Messages ---"
echo ""
top_error=$(grep "ERROR" "$log_file" | awk '{$1=$2=$3=""; print}' | sort | uniq -c | sort -rn | head -5)
echo "$top_error"
echo ""
echo "----------------------------"

```

## Task 5: Summary Report

```bash
date_fmt=$(date +%Y-%m-%d)
report="log_file_${date_fmt}.txt"
total_lines=$(wc -l < "$log_file")

{
echo "===== LOG ANALYSIS REPORT ======"
echo "Date:$date_fmt"
echo "File_Name:$log_file"
echo "Total Lines:$total_lines"
echo "Total Error:$error_count"
echo ""

echo "--- Top 5 Error Messages ---"
echo "$top_error"
echo ""

echo "--- Critical Events ---"
echo "$critical_events"

}> "report"

```

## Task 6: Archive Processed Logs

```bash
Archive_dir="archive"
mkdir -p "$Archive_dir"
mv "$log_file" "$Archive_dir/"
echo "Log File Moved to $Archive_dir"

```
