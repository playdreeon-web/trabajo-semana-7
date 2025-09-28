# trabajo-semana-7
# Proyecto Distribuidora de Alimentos  

Este proyecto corresponde al desarrollo de un prototipo no funcional de aplicación móvil, creado como parte de la Actividad Formativa – Semana 7 del Taller de Aplicaciones (Instituto Profesional AIEP).  

La aplicación busca resolver la necesidad de la empresa distribuidora de alimentos que ofrece despacho a domicilio, aplicando tarifas diferenciadas según el monto de la compra y la distancia del cliente. Además, se considera el monitoreo de la cadena de frío en camiones, lo que permite mantener la calidad de carnes y mariscos.  

## Funcionalidades principales  
- Registro de usuario utilizando cuenta Gmail  
- Carrito de compras para agregar productos  
- Cálculo automático del valor del despacho  
- Monitoreo de temperatura en camiones refrigerados  
- Seguimiento del estado del pedido  

## Prototipo no funcional  
Las pantallas que forman parte del prototipo son:  
1. Inicio de sesión con Gmail
2. agrgar un nuevo usuario 
3. Catálogo de productos  
4. Cálculo automático de despacho  
5. Monitoreo de temperatura 
6. Estado de despacho  

![imagen URL](https://github.com/playdreeon-web/trabajo-semana-7/blob/main/Captura%20de%20pantalla%202025-09-28%20102408.png)
![imagen URL](https://github.com/playdreeon-web/trabajo-semana-7/blob/main/Captura%20de%20pantalla%202025-09-28%20151250.png)


## Modelo Canvas  
[El modelo de negocios se encuentra documentado en `/docs/modelo_canvas.md`.  
](https://github.com/playdreeon-web/trabajo-semana-7/blob/main/modelo%20de%20negocio%20camvas)
## Ejemplo de código  
En la carpeta `/codigo` se incluye un ejemplo en Java que realiza la conversión de grados a radianes, como evidencia del proceso de compilación.  

Para ejecutar:  

// Clase para representar un producto
data class Producto(
    val nombre: String,
    val precio: Int,
    var cantidad: Int
)

// Función que calcula el costo de despacho según reglas del caso
fun calcularDespacho(totalCompra: Int, distanciaKm: Int): Int {
    return when {
        totalCompra >= 50000 -> 0
        totalCompra in 25000..49999 -> 150 * distanciaKm
        else -> 300 * distanciaKm
    }
}

// Ejemplo de uso
fun main() {
    // Lista de productos en el carrito
    val carrito = listOf(
        Producto("Carne congelada", 11000, 2),
        Producto("Cerveza", 6000, 3),
        Producto("Whisky", 25000, 1)
    )

    // Calcular total de la compra
    val totalCompra = carrito.sumOf { it.precio * it.cantidad }
    println("Total compra: $$totalCompra")

    // Supongamos distancia de 12 km
    val distanciaKm = 12
    val costoDespacho = calcularDespacho(totalCompra, distanciaKm)

    val totalFinal = totalCompra + costoDespacho
    println("Costo de despacho: $$costoDespacho")
    println("Total a pagar: $$totalFinal")
}
ejemplo salida 
Total compra: $67000
Costo de despacho: $0
Total a pagar: $67000

ejemplo monitor de temperatura 
fun verificarTemperatura(temp: Double) {
    if (temp > -5) {
        println(" Alerta: La temperatura es $temp°C, riesgo de romper la cadena de frío")
    } else {
        println("Temperatura adecuada: $temp°C")
    }
}

