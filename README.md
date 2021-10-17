# Evidencia
from collections import namedtuple


switch = True
diccionario_registro = {}
diccionario_ventas = {}
Articulo = namedtuple("Venta", ("folio", "fecha"))
Detalle = namedtuple("Folio", ("Descripcion", "Cantidad", "Precio"))


while switch:

    print("--------------MENU REGISTRO DE VENTAS-----------")
    print("¿Qué desea realizar?")
    print("1: Registrar una venta ")
    print("2: Ver ventas ")
    print("3: Consultar una venta")
    print("4: Salir del programa")
    opcion = input("Ingrese una opción: ")

    if opcion == "1":

        folio = input("Ingrese su folio: ")
        if not folio in diccionario_registro.keys():
            fecha = input("Ingrese la fecha: ")
            articulo_registrado = Articulo(folio, fecha)
            diccionario_registro[folio] = articulo_registrado
            
            #folio2=input("ingresa el ID del articulo: ")
            descripcion=input("Ingrese la descripcion: ")
            cantidad=int(input("Ingrese la cantidad: "))
            precio=int(input("Ingrese el precio: "))
            Venta_Registrada=Detalle(descripcion,cantidad,precio)
            diccionario_ventas[folio]=Venta_Registrada
            iva=(precio*cantidad)*0.16
            total=(precio*cantidad)+iva
            print("El total con iva incluido es: ",total) 
    
        else:

            print("Esta venta ya está registrada, intente de nuevo. ")

    elif opcion == "2":

        for folio in diccionario_registro.keys():
            for Folio2 in diccionario_ventas.keys():
                print(f"La venta es: {folio} ")
                print(f"El folio es: {diccionario_registro[folio].folio} ")
                print(f"La fecha es: {diccionario_registro[folio].fecha}")
                print(f"Descripcion: {diccionario_ventas[folio].Descripcion}")
                print(f"Cantidad: {diccionario_ventas[folio].Cantidad}")
                print(f"Precio: {diccionario_ventas[folio].Precio}")
                print()

    elif opcion == "3":

        busqueda = input("Ingrese su folio a buscar: ")
        if busqueda in diccionario_registro.keys() or busqueda in diccionario_ventas.keys():
            print(f"El folio de la venta es: {diccionario_registro[busqueda].folio}")
            print(f"La fecha de la venta es: {diccionario_registro[busqueda].fecha}")
            print(f"Descripcion: {diccionario_ventas[busqueda].Descripcion}")
            print(f"Cantidad: {diccionario_ventas[busqueda].Cantidad}")
            print(f"Precio: {diccionario_ventas[busqueda].Precio}")

        else:

            print("Clave no registrada. ")

   

    elif opcion == "4":

        print("Saldrás del sistema!")
        
        switch = False
        
    else:

        print("Esa opción no es válida")
