# EJERCICIO 1 - TP INTEGRADOR
# Nombre del cliente
nombre = input("Nombre del cliente: ")

while nombre == "" or not nombre.isalpha():
    nombre = input("Error. Ingrese solo letras: ")

# Cantidad de productos
cantidad = input("Cantidad de productos: ")

while not cantidad.isdigit() or int(cantidad) <= 0:
    cantidad = input("Error. Ingrese un entero positivo: ")

cantidad = int(cantidad)

total_sin_descuento = 0
total_con_descuento = 0

# Productos
for i in range(1, cantidad + 1):

    precio = input(f"Producto {i} - Precio: ")

    while not precio.isdigit():
        precio = input("Error. Ingrese un precio válido: ")

    precio = int(precio)

    descuento = input("Descuento (S/N): ")

    while descuento.lower() not in ["s", "n"]:
        descuento = input("Error. Ingrese S o N: ")

    total_sin_descuento += precio

    if descuento.lower() == "s":
        precio_final = precio * 0.9
    else:
        precio_final = precio

    total_con_descuento += precio_final

# Resultados
ahorro_total = total_sin_descuento - total_con_descuento
promedio = total_con_descuento / cantidad

print("\n----- RESUMEN -----")
print(f"Total sin descuentos: ${total_sin_descuento}")
print(f"Total con descuentos: ${total_con_descuento:.2f}")
print(f"Ahorro total: ${ahorro_total:.2f}")
print(f"Promedio por producto: ${promedio:.2f}")

# EJERCICIO 2 - TP INTEGRADOR

usuario_correcto = "alumno"
clave_correcta = "python123"

intentos = 0
acceso = False

while intentos < 3 and not acceso:
    print(f"\nIntento {intentos + 1}/3")

    usuario = input("Usuario: ")
    clave = input("Clave: ")

    if usuario == usuario_correcto and clave == clave_correcta:
        acceso = True
        print("Acceso concedido.")
    else:
        print("Error: credenciales inválidas.")
        intentos += 1

if not acceso:
    print("Cuenta bloqueada.")

else:
    salir = False

    while not salir:

        print("\n1) Estado  2) Cambiar clave  3) Mensaje  4) Salir")

        opcion = input("Opción: ")

        while not opcion.isdigit():
            print("Error: ingrese un número válido.")
            opcion = input("Opción: ")

        opcion = int(opcion)

        while opcion < 1 or opcion > 4:
            print("Error: opción fuera de rango.")
            opcion = input("Opción: ")

            while not opcion.isdigit():
                print("Error: ingrese un número válido.")
                opcion = input("Opción: ")

            opcion = int(opcion)

        if opcion == 1:
            print("Inscripto")

        elif opcion == 2:

            nueva_clave = input("Nueva clave: ")

            while len(nueva_clave) < 6:
                print("Error: mínimo 6 caracteres.")
                nueva_clave = input("Nueva clave: ")

            confirmacion = input("Confirmar clave: ")

            while confirmacion != nueva_clave:
                print("Error: las claves no coinciden.")
                confirmacion = input("Confirmar clave: ")

            clave_correcta = nueva_clave
            print("Clave cambiada correctamente.")

        elif opcion == 3:
            print("¡Seguí adelante, cada práctica te acerca a tu objetivo!")

        elif opcion == 4:
            print("Saliendo...")
            salir = True

# ejercicio 3 - TP INTEGRADOR

# Operador
operador = input("Nombre del operador: ")

while operador == "" or not operador.isalpha():
    operador = input("Error. Ingrese solo letras: ")

# Turnos
lunes1 = "-"
lunes2 = "-"
lunes3 = "-"
lunes4 = "-"

martes1 = "-"
martes2 = "-"
martes3 = "-"

salir = False

while not salir:

    print("\n1. Reservar turno")
    print("2. Cancelar turno")
    print("3. Ver agenda del día")
    print("4. Ver resumen general")
    print("5. Salir")

    opcion = input("Opción: ")

    while not opcion.isdigit():
        opcion = input("Error. Ingrese una opción válida: ")

    opcion = int(opcion)

    if opcion == 1:

        dia = input("Día (1=Lunes, 2=Martes): ")

        while not dia.isdigit() or int(dia) not in [1, 2]:
            dia = input("Error. Día (1=Lunes, 2=Martes): ")

        dia = int(dia)

        nombre = input("Nombre del paciente: ")

        while nombre == "" or not nombre.isalpha():
            nombre = input("Error. Ingrese solo letras: ")

        reservado = False

        if dia == 1:
            if lunes1 == "-":
                lunes1 = nombre
                reservado = True
            elif lunes2 == "-":
                lunes2 = nombre
                reservado = True
            elif lunes3 == "-":
                lunes3 = nombre
                reservado = True
            elif lunes4 == "-":
                lunes4 = nombre
                reservado = True

        else:
            if martes1 == "-":
                martes1 = nombre
                reservado = True
            elif martes2 == "-":
                martes2 = nombre
                reservado = True
            elif martes3 == "-":
                martes3 = nombre
                reservado = True

        if reservado:
            print("Turno reservado.")
        else:
            print("No hay lugares disponibles.")

    elif opcion == 2:

        dia = input("Día (1=Lunes, 2=Martes): ")

        while not dia.isdigit() or int(dia) not in [1, 2]:
            dia = input("Error. Día (1=Lunes, 2=Martes): ")

        dia = int(dia)

        nombre = input("Nombre del paciente: ")

        while nombre == "" or not nombre.isalpha():
            nombre = input("Error. Ingrese solo letras: ")

        encontrado = False

        if dia == 1:
            if lunes1 == nombre:
                lunes1 = "-"
                encontrado = True
            elif lunes2 == nombre:
                lunes2 = "-"
                encontrado = True
            elif lunes3 == nombre:
                lunes3 = "-"
                encontrado = True
            elif lunes4 == nombre:
                lunes4 = "-"
                encontrado = True

        else:
            if martes1 == nombre:
                martes1 = "-"
                encontrado = True
            elif martes2 == nombre:
                martes2 = "-"
                encontrado = True
            elif martes3 == nombre:
                martes3 = "-"
                encontrado = True

        if encontrado:
            print("Turno cancelado.")
        else:
            print("Paciente no encontrado.")

    elif opcion == 3:

        dia = input("Día (1=Lunes, 2=Martes): ")

        while not dia.isdigit() or int(dia) not in [1, 2]:
            dia = input("Error. Día (1=Lunes, 2=Martes): ")

        dia = int(dia)

        if dia == 1:
            print("\nAgenda Lunes")
            print("Turno 1:", lunes1 if lunes1 != "-" else "Libre")
            print("Turno 2:", lunes2 if lunes2 != "-" else "Libre")
            print("Turno 3:", lunes3 if lunes3 != "-" else "Libre")
            print("Turno 4:", lunes4 if lunes4 != "-" else "Libre")
        else:
            print("\nAgenda Martes")
            print("Turno 1:", martes1 if martes1 != "-" else "Libre")
            print("Turno 2:", martes2 if martes2 != "-" else "Libre")
            print("Turno 3:", martes3 if martes3 != "-" else "Libre")

    elif opcion == 4:

        ocupados_lunes = 0
        ocupados_martes = 0

        if lunes1 != "-":
            ocupados_lunes += 1
        if lunes2 != "-":
            ocupados_lunes += 1
        if lunes3 != "-":
            ocupados_lunes += 1
        if lunes4 != "-":
            ocupados_lunes += 1

        if martes1 != "-":
            ocupados_martes += 1
        if martes2 != "-":
            ocupados_martes += 1
        if martes3 != "-":
            ocupados_martes += 1

        disponibles_lunes = 4 - ocupados_lunes
        disponibles_martes = 3 - ocupados_martes

        print("\nResumen General")
        print("Lunes -> Ocupados:", ocupados_lunes, "Disponibles:", disponibles_lunes)
        print("Martes -> Ocupados:", ocupados_martes, "Disponibles:", disponibles_martes)

        if ocupados_lunes > ocupados_martes:
            print("Día con más turnos: Lunes")
        elif ocupados_martes > ocupados_lunes:
            print("Día con más turnos: Martes")
        else:
            print("Empate entre ambos días")

    elif opcion == 5:
        print("Sistema finalizado.")
        salir = True

    else:
        print("Opción inválida.")

# ejercicio 4 - TP INTEGRADOR

energia = 100
tiempo = 12
cerraduras_abiertas = 0
alarma = False
codigo_parcial = ""

forzar_seguidas = 0
bloqueado = False

agente = input("Nombre del agente: ")

while agente == "" or not agente.isalpha():
    agente = input("Error. Ingrese solo letras: ")

while energia > 0 and tiempo > 0 and cerraduras_abiertas < 3 and not bloqueado:

    print("\n----- ESTADO -----")
    print("Agente:", agente)
    print("Energía:", energia)
    print("Tiempo:", tiempo)
    print("Cerraduras abiertas:", cerraduras_abiertas)
    print("Alarma:", alarma)
    print("Código parcial:", codigo_parcial)

    print("\n1. Forzar cerradura")
    print("2. Hackear panel")
    print("3. Descansar")

    opcion = input("Opción: ")

    while not opcion.isdigit() or int(opcion) < 1 or int(opcion) > 3:
        opcion = input("Error. Ingrese una opción válida: ")

    opcion = int(opcion)

    if opcion == 1:

        forzar_seguidas += 1

        energia -= 20
        tiempo -= 2

        if forzar_seguidas == 3:
            alarma = True
            print("La cerradura se trabó. ¡Alarma activada!")
        else:

            if energia < 40:

                numero = input("Riesgo de alarma. Ingrese un número (1-3): ")

                while not numero.isdigit() or int(numero) < 1 or int(numero) > 3:
                    numero = input("Error. Ingrese un número entre 1 y 3: ")

                numero = int(numero)

                if numero == 3:
                    alarma = True
                    print("¡Se activó la alarma!")

            if not alarma:
                cerraduras_abiertas += 1
                print("Cerradura abierta.")

    elif opcion == 2:

        forzar_seguidas = 0

        energia -= 10
        tiempo -= 3

        print("Hackeando panel...")

        for paso in range(4):
            codigo_parcial += "A"
            print("Paso", paso + 1, "- Código:", codigo_parcial)

        if len(codigo_parcial) >= 8 and cerraduras_abiertas < 3:
            cerraduras_abiertas += 1
            print("¡Se abrió una cerradura automáticamente!")

    elif opcion == 3:

        forzar_seguidas = 0

        energia += 15

        if energia > 100:
            energia = 100

        tiempo -= 1

        if alarma:
            energia -= 10

        print("Descansaste.")

    if alarma and tiempo <= 3 and cerraduras_abiertas < 3:
        bloqueado = True

if cerraduras_abiertas == 3:
    print("\n¡VICTORIA! Abriste la bóveda.")

elif bloqueado:
    print("\nDERROTA. El sistema se bloqueó por la alarma.")

else:
    print("\nDERROTA. Te quedaste sin energía o sin tiempo.")

# ejercicio 5 - TP INTEGRADOR

print("--- BIENVENIDO A LA ARENA ---")

nombre_gladiador = input("Nombre del Gladiador: ")

while not nombre_gladiador.isalpha():
    print("Error: Solo se permiten letras.")
    nombre_gladiador = input("Nombre del Gladiador: ")

vida_jugador = 100
vida_enemigo = 100
pociones = 3
ataque_pesado = 15
ataque_enemigo = 12
turno_gladiador = True
juego_activo = True

print("\n=== INICIO DEL COMBATE ===")

while vida_jugador > 0 and vida_enemigo > 0:

    print(f"\n{nombre_gladiador} (HP: {vida_jugador}) vs Enemigo (HP: {vida_enemigo}) | Pociones: {pociones}")
    print("Elige acción:")
    print("1. Ataque Pesado")
    print("2. Ráfaga Veloz")
    print("3. Curar")

    opcion = input("Opción: ")

    while (not opcion.isdigit()) or (opcion.isdigit() and int(opcion) not in [1, 2, 3]):
        if not opcion.isdigit():
            print("Error: Ingrese un número válido.")
        else:
            print("Error: La opción debe ser 1, 2 o 3.")
        opcion = input("Opción: ")

    opcion = int(opcion)

    turno_perdido = False

    if opcion == 1:
        es_critico = vida_enemigo < 20

        if es_critico:
            daño_final = ataque_pesado * 1.5
            print(">> ¡GOLPE CRÍTICO!")
        else:
            daño_final = ataque_pesado * 1.0

        vida_enemigo -= daño_final
        print(f"¡Atacaste al enemigo por {daño_final} puntos de daño!")

    elif opcion == 2:
        print(">> ¡Inicias una ráfaga de golpes!")
        for golpe in range(3):
            vida_enemigo -= 5
            print(" > Golpe conectado por 5 de daño")

    elif opcion == 3:
        if pociones > 0:
            vida_jugador += 30
            pociones -= 1
            print("¡Usaste una poción y recuperaste 30 puntos de vida!")
        else:
            print("¡No quedan pociones!")
            turno_perdido = True

    if vida_enemigo > 0:
        vida_jugador -= ataque_enemigo
        print(f"¡El enemigo te atacó por {ataque_enemigo} puntos de daño!")

    print("=== NUEVO TURNO ===")

if vida_jugador > 0:
    print(f"\n¡VICTORIA! {nombre_gladiador} ha ganado la batalla.")
else:
    print("\nDERROTA. Has caído en combate.")