# Clear Windows Print Spooler Queue

net stop spooler : Stops the Windows Print Spooler service
del /Q /F /S "%systemroot%\System32\spool\PRINTERS\*.*" : Deletes the queued print-job files
/Q: Quiet mode (no confirmation)
/F: Force deletion
/S: Inlcudes files in subdirectories
net start spooler : Starts the Print Spooler service again

## Purpose: 
Clears stuck/pending print jobs by stopping the Print Spooler, deleting the printer queue files, and starting the Spooler again.

## When to use: 
When a printer is stuck on "Printing," "Deleting," "Pending," or jobs won't clear from the print queue.

Run as an Admin

## Quick Reference: Stop Spooler → Clear Queue → Start Spooler



