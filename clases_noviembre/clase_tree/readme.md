# CICLO WHILE 

## Corredor

Sub prueba()

    x = 3
    While x <> 12
        Hoja1.Cells(3, x) = "josymar"
        Hoja1.Cells(3, x - 1) = ""
        For i = 1 To 60000000
        Next i
        x = x + 1
        
    Wend
End Sub    