# Septiembre 20 de 2021

Clases de funcion con diferentes variable

# Visual Basic

``

    Function misnotas(a, b, c, d, e)
    promedio = (a + b + c + d + e) / 5
    
    If (promedio > 7) Then
        misnotas = "con la nota " & promedio & " el estudiante aprobo "
    Else
        misnotas = "con la nota " & promedio & " el estudiante reprobo "
    End If
    End Function
