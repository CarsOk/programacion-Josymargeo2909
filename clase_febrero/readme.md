# Formulario de Registro de Votacion


## Codigo Registro

    Private Sub btnborrar_Click()
        datos.Rows(confi.Cells(1, 2)).EntireRow.Delete
    End Sub


    Private Sub btnbuscar_Click()
        forbuscar.Show
    End Sub

    Private Sub btnconf_Click()
        Application.Visible = True
    End Sub

    Private Sub btneditar_Click()
        activar (True)
    End Sub

    Private Sub btnfoto_Click()
        archivo = Application.GetOpenFilename("Imágenes (*.jpg;*.bmp), *.jpg;*.bmp")
        foto.Picture = LoadPicture(archivo)
        datos.Cells(confi.Cells(1, 2), 4) = archivo
    
    End Sub

    Private Sub btnguardar_Click()
        If txtcedula.Text <> "" And txtnombre.Text <> "" And txtmesa.Text <> "" Then
            datos.Cells(confi.Cells(1, 2), 1) = txtcedula.Text
            datos.Cells(confi.Cells(1, 2), 2) = txtnombre.Text
            datos.Cells(confi.Cells(1, 2), 3) = txtmesa.Text
        MsgBox " datos guardados "
            limpiar
            activar (False)
        Else
            MsgBox " no puede dejar campos vacio "
        End If
    End Sub

    Private Sub btnnuevo_Click()
        confi.Cells(1, 2) = confi.Cells(1, 2) + 1
        confi.Cells(2, 2) = confi.Cells(1, 2)
        activar (True)
        txtcedula.SetFocus
        foto.Picture = LoadPicture("")
    
    End Sub
    Function activar(estado)
        btnguardar.Enabled = estado
        txtcedula.Locked = Not estado
        txtnombre.Locked = Not estado
        txtmesa.Locked = Not estado
        btnnuevo.Enabled = Not estado
        btnfoto.Enabled = estado
    End Function
    Function limpiar()
        txtcedula.Text = empy
        txtnombre.Text = empy
        txtmesa.Text = empy
    End Function

## Codigo de Buscar

    Private Sub btnbuscar_Click()
        x = 3
        ultimo = confi.Cells(2, 2)
        encontrar = False
        While x <= ultimo And encontrar = False
            If datos.Cells(x, 1) Like forbuscar.txtcedula.Text Then
                encontrar = True
                confi.Cells(1, 2) = x
            Else
                x = x + 1
            End If
        
        Wend
        If encontrar Then
            forvoto.txtcedula.Text = datos.Cells(x, 1)
            forvoto.txtnombre.Text = datos.Cells(x, 2)
            forvoto.txtmesa.Text = datos.Cells(x, 3)
            forbuscar.Hide
            forbuscar.txtcedula.Text = empy
        Else
            MsgBox "not data "
        End If
    
        forvoto.btneditar.Enabled = True
    End Sub
