# Powershell-File-Renamer

This PowerShell script automates the process of renaming files in a directory based on their creation date. It prompts the user to enter the directory path containing the files to be renamed. Then, it retrieves all files in the specified directory and iterates through each file. For each file, it extracts the creation date and generates a new filename in the format "YYYY-MM-DD-OriginalFileName". Finally, it renames the file with the new filename. This script can be useful for organizing and managing files based on their creation dates.

Here's a unique PowerShell script that automates the process of renaming files in a directory based on specific criteria, such as their creation date:

```powershell
# PowerShell File Renamer

# Function to rename files based on creation date
function Rename-FilesByCreationDate {
    param (
        [string]$path
    )

    # Get all files in the specified directory
    $files = Get-ChildItem -Path $path -File

    # Iterate through each file
    foreach ($file in $files) {
        # Extract the creation date of the file
        $creationDate = $file.CreationTime.ToString("yyyy-MM-dd")

        # Generate a new filename based on the creation date
        $newFilename = "$creationDate-$($file.Name)"

        # Rename the file
        Rename-Item -Path $file.FullName -NewName $newFilename
    }

    Write-Host "File renaming completed."
}

# Main script
$directory = Read-Host "Enter the directory path to rename files:"
Rename-FilesByCreationDate -path $directory
```
