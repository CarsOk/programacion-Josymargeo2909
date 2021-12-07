# Ciclo while suma

Sub ejercicio()
    
    x = 1
    suma = Hoja1.Cells(x, 1) + Hoja1.Cells(x, 2)
    While suma < 1000
        Hoja1.Cells(x, 3) = Hoja1.Cells(x, 1) + Hoja1.Cells(x, 2)
        suma = Hoja1.Cells(x, 3)
        x = x + 1
    Wend
End Sub