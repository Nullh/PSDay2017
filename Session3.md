# Working with different types of data in PowerShell
## Jonathan Medd 

Demo heavy! See github

### Built in cmdlets or use something else? Working with different data:
* [text](#text)
* [csv](#csv)
* [excel](#excel)
* [xml](#xml)
* [JSON](#json)
* [YAML](#yaml)

### Text
Out of the box there's Get-Content and Select-String as well as stream-reader etc.
Get-Content is useful, but may not be suitable for everything. It reads all the file into memory, so if there's a large file then it's not great.
We can drop into .NET and use StreamReader instead.

Select-String -Path .\Data\*.txt -Pattern "3" <- search multiple files for the string "3"

Writing out is via Out-File, Add-Content and Set-Content.
Worth noting that Get-Content locks the file, so you will not be ab;e to write back to it. Out-File is non-locking.
Add-content is append to end.
Encoding can be set with the *-Content commands. It defaults to ASCII.

### CSV
Import-CSV
Watch out for files with no header! You can generate one with the -Header parameter
Export-CSV writhes to CSVs. If you add -NoTypeInformation it will supress the weird first line.
There's also ConvertForm-CSV and ConvertTo-CSV which allow you to work with CSV like data.

### Excel
No native support! Use the following:
Install-Module ImportExcel
Import-Excel (This does not require Excel to be installed!)
Export-Excel <- This has lots of parameters to make your output look nice
Part of this module lets you create charts: New-ExcelChartType then pass definition to Export-Excel

### XML
Import-CliXML is built-in but only used with Export-CliXML, so not really what you want.
Instead use New-Object System.Xml.XmlDocument or [xml] accelerator for Get-Content `[xml]$var = Get-Content .\Data\Test.xml`
You can then use XPath or Object. notation.
For saving XML, you pretty much have to use the save method of the .NET XmlDocument.

### JSON
Get-Content <file> | ConvertFrom-JSON
Then you can drill into that with object. notation.
Also pipe things to ConvertTo-JSON, but don't forget you have to save the file yourself, this is just a conversion!
Defaults to 2 depth, so override this with the -Depth flag.

### YAML
No native support. Use the following:
`Install-Module powershell-yaml`
Gives you ConvertFrom-YAML and ConvertTo-YAML.
Use these similar to the JSON commands above.

### Problems!
What do you do if the data you've been given isn't in one of these formats?
ConvertFrom-String is your friend. You give it a template and it can pull in the data.

### Summary
1. Use built in
2. 3rd party modules via powershell gallery
3. .NET