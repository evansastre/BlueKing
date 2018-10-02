# some  windows\(cygwin\) shows "cp is not recognized "

Issue:

```text
#'cp' is not recognized as an internal or external command
```

Solve:

Add "C:\cygwinroot\bin" to Evironment Variabled

```text
setx Path "%PATH%;C:\cygwinroot\bin" /M
```



