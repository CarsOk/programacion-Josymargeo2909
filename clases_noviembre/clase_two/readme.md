# CICLO WHILE

## VOTACIONES


Sub votacion()

    x = 2

    While Hoja1.Cells(x, 2) <> "N"
    
        If Hoja1.Cells(x, 2) = "S" Then
            Hoja1.Cells(x, 3) = 100000
        ElseIf Hoja1.Cells(x, 2) = "B" Then
            Hoja1.Cells(x, 3) = 50000
        ElseIf Hoja1.Cells(x, 2) = "G" Then
            Hoja1.Cells(x, 3) = 100000
        Else
            MsgBox "¡ERROR¡ Coloque B, G, N y S Gracias"
        End If
        x = x + 1
    Wend
    
End Sub