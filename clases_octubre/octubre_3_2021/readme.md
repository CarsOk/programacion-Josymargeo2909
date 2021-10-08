# Clase 3 de Octubre

## Ciclos For Next

    Sub prueba1()

    For x = 2 To 20 Step 1
        a = datos.Cells(x, 1)
        b = datos.Cells(x, 2)
        c = a + b
        datos.Cells(x, 3) = c
        
        
    Next x
    
 
    End Sub

## Actividad de recorido

    Sub prueba2()
    For x = 6 To 13 Step 1
        
        
        Hoja1.Cells(5, x) = "josymar"
        Hoja1.Cells(5, x) = ""
       
    Next x
    
    For h = 4 To 13 Step 1
        Hoja1.Cells(h, 13) = "josymar peña"
        Hoja1.Cells(h, 13) = ""
       nect h
       
    End Sub