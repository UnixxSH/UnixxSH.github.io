```
      $Shell = New-Object -ComObject ("WScript.Shell")

      $ShortCut = $Shell.CreateShortcut("[[shortcut]].lnk")

      $ShortCut.TargetPath="C:\Program Files\Mozilla Firefox\firefox.exe"

      $ShortCut.Arguments="""-private""" + " " + """[[link]]"""

      $ShortCut.WorkingDirectory = "C:\Program Files\Mozilla Firefox\"

      $ShortCut.Description = "[[desc]]"

      $ShortCut.Save()
```