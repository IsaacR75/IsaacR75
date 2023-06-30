certificados = []
personas = []

def grabar():
    nif = input("Ingrese el NIF: ")
    nombre = input("Ingrese el nombre: ")
    while len(nombre) < 8:
        print("El nombre debe tener al menos 8 caracteres.")
        nombre = input("Ingrese el nombre: ")
    edad = int(input("Ingrese la edad: "))
    while edad < 0:
        print("La edad debe ser mayor o igual a 0.")
        edad = int(input("Ingrese la edad: "))
    
    personas.append({"nif": nif, "nombre": nombre, "edad": edad})
    
    print("Datos guardados correctamente.")

def buscar():
    nif_buscar = input("Ingrese el NIF de la persona a buscar: ")
    persona_encontrada = None
    
    for persona in personas:
        if persona["nif"] == nif_buscar:
            persona_encontrada = persona
            break
    
    if persona_encontrada:
        print("Información encontrada:")
        print("NIF:", persona_encontrada["nif"])
        print("Nombre:", persona_encontrada["nombre"])
        print("Edad:", persona_encontrada["edad"])
        print("Pertenencia a la Unión Europea: Sí" if nif_buscar.startswith("ES") else "No")
    else:
        print("Persona no encontrada.")
        
def imprimir_certificados():
    if len(personas) == 0:
        print("No hay personas registradas.")
        return
    
    certificado_nacimiento = {"nombre": "Certificado de Nacimiento", "nif": "", "datos": ""}
    certificado_estado_conyugal = {"nombre": "Certificado de Estado Conyugal", "nif": "", "datos": ""}
    certificado_union_europea = {"nombre": "Certificado de Pertenencia a la Unión Europea", "nif": "", "datos": ""}
    
    for persona in personas:
        certificado_nacimiento["nif"] = persona["nif"]
        certificado_nacimiento["datos"] = f"Nombre: {persona['nombre']}, Edad: {persona['edad']}"
        certificado_estado_conyugal["nif"] = persona["nif"]
        certificado_estado_conyugal["datos"] = f"Nombre: {persona['nombre']}"
        certificado_union_europea["nif"] = persona["nif"]
        certificado_union_europea["datos"] = f"Nombre: {persona['nombre']}, Pertenencia a la Unión Europea: {'Sí' if persona['nif'].startswith('ES') else 'No'}"
        
        certificados.append(certificado_nacimiento)
        certificados.append(certificado_estado_conyugal)
        certificados.append(certificado_union_europea)
    
    print("Certificados impresos correctamente.")

def salir():
    print("Saliendo del programa...")
    print("Gracias por usar este programa. Hasta luego!")

def main():
    nombre_apellido = "John Doe"
    version_programa = "1.0"
    opcion = 0
    
    while opcion != 4:
        print("----- Menu -----")
        print("1. Grabar")
        print("2. Buscar")
        print("3. Imprimir certificados")
        print("4. Salir")
        
        opcion = int(input("Ingrese una opción: "))
        
        if opcion == 1:
            grabar()
        elif opcion == 2:
            buscar()
        elif opcion == 3:
            imprimir_certificados()
        elif opcion == 4:
            salir()
            break
        else:
            print("Opción inválida. Intente nuevamente.")

    print("Nombre y apellido:", nombre_apellido)
    print("Versión del programa:", version_programa)

if __name__ == "__main__":
    main()
