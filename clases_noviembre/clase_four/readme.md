# CICLO WHILE 

## Suma

Sub prueba()

    Hoja1.Cells(1, 1) = 0
    x = 2
    a = 1
    While a <> 0
        
        a = Int(InputBox("escriba el numero a sumar"))
        Hoja1.Cells(x, 1) = a
        c = Hoja1.Cells(1, 1) + a
        Hoja1.Cells(1, 1) = c
        x = x + 1
        
    Wend
    
End Sub