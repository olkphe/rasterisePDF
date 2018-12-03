# rasterisePDF
Flattening PDF using Ghostscript

If you have a digitally secured PDF and having issue printing it, you might consider rasterise it first. Using command below.

## On Windows
```
gswin64c.exe -sDEVICE=pdfwrite -sOutputFile=output.pdf -dBATCH -dNOPAUSE input.pdf
```

## C#
```C#
ProcessStartInfo startInfo = new ProcessStartInfo();
startInfo.CreateNoWindow = false;
startInfo.UseShellExecute = false;
startInfo.FileName = @"C:\Program Files\gs\gs9.26\bin\gswin64c.exe"; //This path maybe vary, check the Ghostscript platform you installed
startInfo.WindowStyle = ProcessWindowStyle.Hidden;
startInfo.Arguments = "-sDEVICE=pdfwrite -sOutputFile=\"" + pdfOutput + "\" -dBATCH -dNOPAUSE \"" + fullfilepath + "\"";

try
{
  // Start the process with the info we specified.
  // Call WaitForExit and then the using-statement will close.
  using (Process exeProcess = Process.Start(startInfo))
  {
      exeProcess.WaitForExit();
      
      //This will delete the old output and replace with the new
      if (File.Exists(pdfOutput))
      {
          if (File.Exists(fullfilepath))
          {
              File.Delete(fullfilepath);
              File.Move(pdfOutput, fullfilepath);
          }
      }
  }
}
catch (Exception ex)
{
  // Log error.
  Console.WriteLine(ex.Message);
}
```

[Ghostscript](https://www.ghostscript.com/) is required. 
