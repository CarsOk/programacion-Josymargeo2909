# clase 11 de octubre

## ciclo for con colores

Private Sub CommandButton1_Change()
Dim a As String


a = InputBox("Que comience el juego")


    For x = 2 To 10 Step 1
    
    Hoja1.Cells(x - 1, x - 1) = empy
    Hoja1.Cells(x, x).Interior.Color = RGB(160, 248, 162)
    Hoja1.Cells(x, x) = a
    
    
        For k = 1 To 50000000
        Next k
    Next x
    
    For i = 9 To 1 Step -1
    Hoja1.Cells(i, 10) = a
    Hoja1.Cells(i, 10).Interior.Color = RGB(222, 234, 72)
    Hoja1.Cells(i + 1, 10) = ""
    
    
        For k = 1 To 40000000
        Next k
    Next i
    
    For h = 10 To 1 Step -1
    Hoja1.Cells(1, h + 1) = ""
    Hoja1.Cells(1, h).Interior.Color = RGB(67, 163, 243)
    Hoja1.Cells(1, h) = a
    
        For k = 1 To 40000000
        Next k
    Next h
    Hoja1.Cells(1, 1) = ""
MsgBox "gracias por participar"
End Sub
