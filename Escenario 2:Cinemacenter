# SISTEMA DE RESERVAS DE CINENACENTER

def realizar_reserva():
    #butacas de cada sala como maximo
    cap_dune_18 = 50
    cap_dune_21 = 50
    cap_deadpool_18 = 50
    cap_deadpool_21 = 50
    #precio de cada entrada
    precio_base = 5000.0
    continuar = "s"
    archivo = open("reservas.txt", "a")
    #bucle para continauar haciendo reservas
    while continuar == "s" or continuar == "S":
        #menu para que el usuario elija pel y hor
        print("\n NUEVA RESERVA ")
        print("Películas: 1. Dune  | 2. Deadpool")
        op_peli = input("Seleccione película (1 o 2): ")
        print("Horarios: 1. 18:00 | 2. 21:30")
        op_horario = input("Seleccione horario (1 o 2): ")
        cantidad_str = input("Cantidad de entradas a comprar: ")
        cantidad = int(cantidad_str)
        #variables para saber si la reserva es valida y guardarlo
        reserva_valida = False
        nombre_peli = ""
        nombre_horario = ""
        #condicional para elegir la peli y el horario de dune y deadpool
        if op_peli == "1":
            nombre_peli = "Dune "
            if op_horario == "1" and cantidad <= cap_dune_18:
                cap_dune_18 = cap_dune_18 - cantidad
                nombre_horario = "18:00"
                reserva_valida = True
            elif op_horario == "2" and cantidad <= cap_dune_21:
                cap_dune_21 = cap_dune_21 - cantidad
                nombre_horario = "21:30"
                reserva_valida = True
        elif op_peli == "2":
            nombre_peli = "Deadpool"
            if op_horario == "1" and cantidad <= cap_deadpool_18:
                cap_deadpool_18 = cap_deadpool_18 - cantidad
                nombre_horario = "18:00"
                reserva_valida = True
            elif op_horario == "2" and cantidad <= cap_deadpool_21:
                cap_deadpool_21 = cap_deadpool_21 - cantidad
                nombre_horario = "21:30"
                reserva_valida = True
                #si la reserva fue valida calcuilo el total
        if reserva_valida == True:
            total = cantidad * precio_base   
            print("Reserva exitosa. Total a pagar: $", total)
            archivo.write(nombre_peli + "\n")
            archivo.write(nombre_horario + "\n")
            archivo.write(str(cantidad) + "\n")
        else:
            print("Error: Selección inválida o capacidad insuficiente en la sala.")  
        #hacer otra reserva o salir del bucle
        print("\n¿Desea hacer otra reserva? (s/n): ")
        continuar = input()
    archivo.close()
    #es una funcion de estadistica
def mostrar_estadisticas_corte_control():
    print("\n ESTADÍSTICAS")
    archivo = open("reservas.txt", "r")
    peli_leida = archivo.readline()
    if peli_leida == "":
        print("No hay registros de ventas en el archivo.")
        # si esta vacio o tiene espacio en blanco toma como que no hay nada
    else:
        total_general_entradas = 0
        max_ventas_peli = -1
        peli_mas_elegida = ""
        total_horario_18 = 0
        total_horario_21 = 0
        while peli_leida != "":
            peli_actual = peli_leida
            total_entradas_peli = 0
            print("\nProcesando totales por película.")
            while peli_leida != "" and peli_leida == peli_actual:
                horario_leido = archivo.readline()
                cantidad_str = archivo.readline()
                cantidad = int(cantidad_str)
                total_entradas_peli = total_entradas_peli + cantidad
                total_general_entradas = total_general_entradas + cantidad
                if horario_leido == "18:00\n":
                    total_horario_18 = total_horario_18 + cantidad
                elif horario_leido == "21:30\n":
                    total_horario_21 = total_horario_21 + cantidad      
                peli_leida = archivo.readline()
            if total_entradas_peli > max_ventas_peli:
                max_ventas_peli = total_entradas_peli
                peli_mas_elegida = peli_actual
        if total_horario_18 > total_horario_21:
            horario_mas_demandado = "18:00"
        elif total_horario_21 > total_horario_18:
            horario_mas_demandado = "21:30"
        else:
            horario_mas_demandado = "Ambos por igual"   
        print(" ESTADISTICAS CINEMACENTER")
        print("Total general de entradas:", total_general_entradas)
        print("Película más elegida:", peli_mas_elegida, "(", max_ventas_peli, "entradas)")

        print("Horario con mayor demanda:", horario_mas_demandado)
    archivo.close()
archivo_inicial = open("reservas.txt", "a")
archivo_inicial.close()
opcion = "0"
while opcion != "3":
    print("\nMENÚ PRINCIPAL")

    print("1. Realizar Reservas")
    print("2. Ver Estadísticas ")
    print("3. Salir")
    opcion = input("Seleccione una opción (1-3): ")
    if opcion == "1":
        realizar_reserva()
    elif opcion == "2":
        mostrar_estadisticas_corte_control()
    elif opcion == "3":
        print("Saliendo del sistema de reservas. ¡Hasta luego!")
    else:
        print("Opción inválida. Intente nuevamente.")
# Vamos gano argentina
