# Diff Settings

You can diff any two locations, meaning two servers, two JSON files, a server and a JSON file, etc, etc.

```text
cfconfig diff server1 server2
cfconfig diff file1.json file2.json
cfconfig diff servername file.json
cfconfig diff from=path/to/servers1/home to=path/to/server2/home
```

You can even filter what config settings you see:

```text
cfconfig diff to=serverName --all
cfconfig diff to=serverName --valuesDiffer --toOnly --fromOnly
```

## Diff Reports

The `cfconfig diff` commandbox has the ability to export HTML and PDF files.  The contents of the report will exactly match what displays in the CLI.  So any flags you apply such as `--toOnly` will also filter the report output.  This can be handy for historical purposes or just to get the data into a format that's easier to read than the CLI.

To generate an HTML report: 

```bash
cfconfig diff to=... from=... HTMLReportPath=folder/
cfconfig diff to=... from=... HTMLReportPath=folder/file.html
```

To generate a PDF report: 

```bash
cfconfig diff to=... from=... PDFReportPath=folder/
cfconfig diff to=... from=... PDFReportPath=folder/file.pdf
```

You can generate both HTML and PDF at the same time if you like.  If you don't provide a filename, one is created for you with the following format:

```text
cfconfig-diff-report-YYYY-MM-DD-HHMMSS.[html|pdf]
```

  The report directory is also created for you if it doesn't exist.

Remember, you can get funky and generate clever report names on the fly such as:

```bash
cfconfig diff ... PDFreportpath="Daily-Report-`#now | #dayOfWeek | #dayOfWeekAsString`.pdf"
```

This would give you a name like `Daily-Report-Thursday.pdf`!  Existing files are overwritten.

