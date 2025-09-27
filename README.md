"""
Módulo: vehiculos.py
--------------------
Este módulo modela vehículos utilizando Programación Orientada a Objetos (POO) en Python.

Incluye:
- Una clase base Vehiculo.
- Dos subclases: Coche y Moto.
- Implementación de herencia, encapsulamiento y polimorfismo.
- Métodos comunes (acelerar, frenar) y específicos (mostrar_datos, consumo_combustible).
- Ejemplo de uso al final del archivo.

Objetivo: 
Que el estudiante practique clases, atributos, métodos, herencia, polimorfismo y encapsulamiento.

Autor: [Tu Nombre]
Fecha: Septiembre 2025
"""

class Vehiculo:
    """
    Clase base que representa un vehículo genérico.
    Contiene atributos y métodos comunes a todos los vehículos.
    """

    def __init__(self, marca: str):
        """
        Constructor de Vehiculo.

        Parámetros:
        - marca (str): La marca del vehículo.
        """
        self.__marca = marca        # Atributo privado: marca
        self.__velocidad = 0        # Atributo privado: velocidad inicial en km/h

    # Métodos de acceso a atributos privados (encapsulamiento)
    def get_marca(self):
        return self.__marca

    def get_velocidad(self):
        return self.__velocidad

    def set_velocidad(self, nueva_velocidad):
        """
        Permite modificar la velocidad del vehículo.
        Se asegura de que no sea negativa.
        """
        if nueva_velocidad < 0:
            self.__velocidad = 0
        else:
            self.__velocidad = nueva_velocidad

    # Métodos comunes
    def acelerar(self, incremento: int):
        """
        Aumenta la velocidad del vehículo.

        Parámetros:
        - incremento (int): valor en km/h que se suma a la velocidad actual.
        """
        self.set_velocidad(self.get_velocidad() + incremento)

    def frenar(self, decremento: int):
        """
        Disminuye la velocidad del vehículo.

        Parámetros:
        - decremento (int): valor en km/h que se resta a la velocidad actual.
        """
        self.set_velocidad(self.get_velocidad() - decremento)

    def mostrar_datos(self):
        """
        Método genérico para mostrar datos del vehículo.
        Será sobrescrito en las subclases.
        """
        print(f"Marca: {self.get_marca()} | Velocidad: {self.get_velocidad()} km/h")

    def consumo_combustible(self, distancia: float):
        """
        Método genérico para calcular el consumo de combustible.
        Será sobrescrito en las subclases.

        Parámetros:
        - distancia (float): kilómetros recorridos.

        Retorna:
        - Consumo estimado en litros (float).
        """
        return 0.0


class Coche(Vehiculo):
    """
    Subclase que representa un coche.
    Hereda de Vehiculo e incluye atributos adicionales.
    """

    def __init__(self, marca: str, puertas: int = 4):
        """
        Constructor de Coche.

        Parámetros:
        - marca (str): marca del coche.
        - puertas (int): número de puertas (default = 4).
        """
        super().__init__(marca)
        self.__puertas = puertas  # Atributo privado: número de puertas

    def mostrar_datos(self):
        """
        Muestra la información específica de un coche.
        Sobrescribe al método de la clase base.
        """
        print(f"🚗 Coche - Marca: {self.get_marca()} | Velocidad: {self.get_velocidad()} km/h | Puertas: {self.__puertas}")

    def consumo_combustible(self, distancia: float):
        """
        Calcula el consumo de combustible del coche.

        Suposición:
        - Rendimiento promedio: 15 km/L.
        """
        rendimiento = 15
        return round(distancia / rendimiento, 2)


class Moto(Vehiculo):
    """
    Subclase que representa una moto.
    Hereda de Vehiculo e incluye atributos adicionales.
    """

    def __init__(self, marca: str, tipo_casco: str = "Integral"):
        """
        Constructor de Moto.

        Parámetros:
        - marca (str): marca de la moto.
        - tipo_casco (str): tipo de casco recomendado (default = "Integral").
        """
        super().__init__(marca)
        self.__tipo_casco = tipo_casco  # Atributo privado: tipo de casco recomendado

    def mostrar_datos(self):
        """
        Muestra la información específica de una moto.
        Sobrescribe al método de la clase base.
        """
        print(f"🏍️ Moto - Marca: {self.get_marca()} | Velocidad: {self.get_velocidad()} km/h | Casco recomendado: {self.__tipo_casco}")

    def consumo_combustible(self, distancia: float):
        """
        Calcula el consumo de combustible de la moto.

        Suposición:
        - Rendimiento promedio: 30 km/L.
        """
        rendimiento = 30
        return round(distancia / rendimiento, 2)


# Ejecución de prueba
if __name__ == "__main__":
    # Crear un coche
    mi_coche = Coche("Toyota", 4)
    mi_coche.acelerar(60)
    mi_coche.mostrar_datos()
    print(f"Consumo del coche en 150 km: {mi_coche.consumo_combustible(150)} L")
    mi_coche.frenar(30)
    mi_coche.mostrar_datos()

    print("-" * 50)

    # Crear una moto
    mi_moto = Moto("Yamaha", "Abierto")
    mi_moto.acelerar(80)
    mi_moto.mostrar_datos()
    print(f"Consumo de la moto en 150 km: {mi_moto.consumo_combustible(150)} L")
    mi_moto.frenar(50)
    mi_moto.mostrar_datos()
.
