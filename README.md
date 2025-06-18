turistas = {
    '001': ['John Doe', 'Estados Unidos', '12-01-2024'],
    '002': ['Emily Smith', 'Estados Unidos', '23-03-2024'],
    '012': ['Julian Martinez', 'Argentina', '19-09-2023'],
    '014': ['Agustin Morales', 'Argentina', '28-03-2024'],
    '005': ['Carlos Garcia', 'Mexico', '10-05-2024'],
    '006': ['Maria Lopez', 'Mexico', '08-12-2023'],
    '007': ['Joao Silva', 'Brasil', '20-06-2024'],
    '003': ['Michael Brown', 'Estados Unidos', '05-07-2023'],
    '004': ['Jessica Davis', 'Estados Unidos', '15-11-2024'],
    '008': ['Ana Santos', 'Brasil', '03-10-2023'],
    '010': ['Martin Fernandez', 'Argentina', '13-02-2023'],
    '011': ['Sofia Gomez', 'Argentina', '07-04-2024'],
}

def menu():
    print('**MENU PRINCIPAL**')
    print('1.- Turistas por Pais')
    print('2.- Turistas por Mes')
    print('3.- Eliminar Turista')
    print('4.- Salir')

# Opción 1
def turistasporelpais():
    pais = input('Seleccione el país: ').strip()
    encontrados = False

    for datos in turistas.values():
        if datos[1].lower() == pais.lower():
            print(f'Nombre: {datos[0]}, Fecha: {datos[2]}')
            encontrados = True
    if not encontrados:
        print('No se encontraron turistas del país, Por favor ingrese uno que esté en la lista presente')




# Opción 2
def turistaspormes(mes):
    TOTALturistas = len(turistas)
    turistasChile = 0
    for datos in turistas.values():
        fecha = datos[2]
        MesTurista = int(fecha.split('-')[1])
        if MesTurista == mes:
            turistasChile += 1
    if TOTALturistas == 0:
        return 0.0
    
    porcentaje = round((turistasChile / TOTALturistas) * 100, 1)
    return porcentaje





# Opción 3
def Eliminarturista():
    eliminar = input('Ingrese el nombre del turista que desea eliminar: ').strip().lower()
    claveturista = None
    
    
    for clave, datos in turistas.items():
        if datos[0].lower() == eliminar:
            claveturista = clave
            break

    if claveturista:
        del turistas[claveturista]
        print('Turista eliminado')
    else:
        print('Turista no encontrado, No se logro eliminar')



def main():
    while True:
        menu()
        opciones = input('Seleccione una de las opciones: ').strip()  
        if opciones == '1':
            turistasporelpais()  
        elif opciones == '2':
            while True:
                Mes12 = input('Ingrese un mes (1-12): ').strip()
                if Mes12.isdigit():
                    mes = int(Mes12)  
                    if 1 <= mes <= 12:
                        break
                    else:
                        print('Ingrese un mes válido entre 1 y 12, vuelva a intentar.')
                else:
                    print('Ingrese un número válido, vuelva a intentar.')
            porcentaje = turistaspormes(mes)
            print(f'\n{porcentaje}% de turistas visitaron Chile en el mes {mes}.')
        elif opciones == '3':
            Eliminarturista()
        elif opciones == '4':
            print('Saliendo del programa.')
            break
        else:
            print('Opción no válida, vuelva a intentar e ingrese alguna de las opciones.')



if __name__ == '__main__':
    main()
