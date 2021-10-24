# ciclo while

    Private Sub CommandButton1_Click()
    micombo.Clear

    fila = 5

    While Hoja1.Cells(fila, 4) <> ""
    micombo.AddItem Hoja1.Cells(fila, 4)

    fila = fila + 1

    Wend

    End Sub

## ejercicio

Private Sub CommandButton1_Click()

    Dim ala As Integer, num As Integer, fila As Integer
    fila = 2
    ala = Math.Rnd * 100  'forma alateorio

    'Debug.Print ala para que salga en la ventana inmediato

    While ala <> num

    num = InputBox("introduce numero de 1 a 100", "introduccion", "nº", 100, 100) 'propiedades y ubicacion

    Hoja1.Cells(fila, 4) = num

    If ala > num Then
    
        Hoja1.Cells(fila, 6) = "el numero es mas alto"
    
    ElseIf ala < num Then
    
        Hoja1.Cells(fila, 6) = "el numero es mas bajo"
    
    Else
    
        With Hoja1.Cells(fila, 6) 'manipular propiedades
        .Value = "correcto"
        .Font.Color = vbGreen  'color fijo siempre va con vb tambuien puede ser con rgb
        .Font.Size = 36 ' tamaño de texto
    End With
    
    End If

    Hoja1.Cells(fila, 8) = fila - 1

    fila = fila + 1 ' contador

    Wend

End Sub

    Private Sub CommandButton2_Click()

    Hoja1.Cells(2, 4).Select    'seleccionando el rango y borrarlo hacia abajo
    Range(Selection, Selection.End(xlDown)).Select
    Selection.Clear

    Hoja1.Cells(2, 6).Select
    Range(Selection, Selection.End(xlDown)).Select
    Selection.Clear

    Hoja1.Cells(2, 8).Select
    Range(Selection, Selection.End(xlDown)).Select
    Selection.Clear

End Sub
