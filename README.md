# consumo_de_energia
## Para administrar la nueva matriz energética del Ecuador, Ud. tiene un diccionario con la información de las 
plantas de energía y a las ciudades que atienden. ​Cada ciudad tiene: una tupla con los consumos mensuales
(12) del año en ​megavatios-hora (MWh) y la tarifa de consumo en dólares por megavatio-hora (MWh) que le
cobra la planta eléctrica. Una ciudad puede estar servida por más de una planta eléctrica. No todas las 
ciudades​ ​son​ ​servidas​ ​por​ ​todas​ ​las​ ​plantas​ ​eléctricas.

```python
consumo_energia = {
    'Coca Codo Sinclair':{
        'Quito': {'consumos': (400, 432, 400, 420, 432, 460, 432, 400, 432, 300, 213), 'tarifa': 65},
        'Guayaquil': {'consumos': (120, 55, 32, 120, 75, 32, 150, 55, 32, 120, 97, 32),'tarifa': 84}
    },
    'Sopladora': {
        'Guayaquil':{ 'consumos': (310, 220, 321, 310, 220, 321, 310, 220, 321, 310, 220, 321),'tarifa':55},
        'Quito': { 'consumos': (400, 432, 587, 400, 432, 587, 400, 432, 587, 400, 432, 587),'tarifa': 79},
        'Tena': { 'consumos': (50, 32, 32, 50, 32, 32, 50, 32, 32, 50, 32, 32),'tarifa': 32},
        'Loja': { 'consumos': (50, 32, 32, 50, 32, 32, 50, 32, 32, 50, 32, 32),'tarifa': 32},
        'Manta': { 'consumos': (50, 32, 32, 50, 32, 32, 50, 32, 32, 50, 32, 32),'tarifa': 32},
        'Puerto Ayora': { 'consumos': (50, 50),'tarifa': 10}
 },
}

informacion = {
    'Costa': ('Guayaquil', 'Manta'),
    'Sierra': ('Quito', 'Ambato', 'Loja'),
    'Oriente': ('Tena', 'Nueva Loja')
}

informacion['Insular'] = ('Puerto Ayora', 'Puerto Villamil')

def total_consumo_por_planta_ciudad(planta, ciudad):
    if planta not in consumo_energia.keys():
        return 'La planta ' + planta + ' no existe'

    if ciudad not in consumo_energia[planta].keys():
        return 'La planta ' + planta + ' no proveé energía a la ciudad de ' + ciudad

    total_consumo = sum(consumo_energia[planta][ciudad]['consumos'])
    return total_consumo

def total_consumo_ciudad(ciudad):
      
    if ciudad not in consumo_energia['Coca Codo Sinclair'].keys():
        return 'No hay planta de Coca Codo Sinclair en ' + ciudad


    total_consumo2 = sum(consumo_energia['Coca Codo Sinclair'][ciudad]['consumos'])
    print( 'El consumo de energía de la planta Coca Codo Sinclair en la ciudad de',ciudad,total_consumo2,"MWh")

def total_consumo_ciudad1(ciudad):
    if ciudad not in consumo_energia['Sopladora'].keys():
        return 'No hay planta de Sopladora en ' + ciudad

    total_consumo2 = sum(consumo_energia['Sopladora'][ciudad]['consumos'])
    print( 'El consumo de energía de la planta Sopladora en la ciudad de',ciudad,total_consumo2,"MWh")

def total_por_region(region):
    if region not in informacion.keys():
        return 'region no existe'
        
    ciudades_region = informacion[region]
    total_consumo = 0
    for ciudad_region in ciudades_region:
        for planta in consumo_energia.keys():
            for ciudad in consumo_energia[planta].keys():
                if ciudad_region ==  ciudad:
                    total_consumo += sum(consumo_energia[planta][ciudad]['consumos']) * consumo_energia[planta][ciudad]['tarifa']

    return total_consumo

op = -1
while op != 0:

    print('<1> Total de energía consumida por planta y ciudad')
    print('<2>. Total de Energia por Ciudad ')
    print('<3>. Dinero Recaudado por Region ')
    print('<4> Salir')

    op = int(input('Ingrese opción:'))
    
    
    if op == 1:
        print('''
    .........Total de megavatios en la planta: Coca Codo Sinclair,Sopladora ............
    ''')
        planta = input('Ingrese el nombre de la planta:')
        ciudad = input('Ingrese el nombre de la ciudad:')

        total = total_consumo_por_planta_ciudad(planta, ciudad)

        if type(total) == int:
            print('El consumo de energía en la ciudad de {} fue de {} MWh en la planta {}'.format(ciudad, total, planta))
        else:
            print(total)

    elif op == 2:
        print('''
       ....Total de energia dada a cada ciudad por planta 
        CIUDADES:Guayaquil, Quito, Loja, Ambato, Tena, Nueva loja, Manta.....
    ''')
        ciudad = input('Ingrese el nombre de la ciudad:')
        total = total_consumo_ciudad(ciudad)
        total1 = total_consumo_ciudad1(ciudad)
        if type(total and total1)==int:
            print(total)
            print(total1)
        else:
            print(total)
            print(total1)
   
    elif op == 3:
        print('''
    .....Dinero recaudado 
    Regiones: Costa, Sierra, Oriente, Insular......
    ''')
        region = input('Ingrese región:')
        total2 = total_por_region(region)
        if type(total2)==int:
            print("La Region",region, 'recaudo:', total2,"Dolares$", '\n')
        else:
            print(total2)
  
        ```
