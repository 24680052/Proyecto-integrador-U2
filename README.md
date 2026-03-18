# Proyecto-integrador-U2 
## Tienda Tecnologica con flet
Este repositorio presenta el desarrollo de una aplicación gráfica creada con Python y Flet, cuyo objetivo es mostrar una lista de productos tecnológicos mediante una interfaz moderna basada en componentes reutilizables.

La aplicación utiliza una estructura de datos que contiene varios productos, los cuales se muestran dinámicamente en pantalla mediante tarjetas de producto personalizadas. Cada tarjeta incluye imagen, nombre, descripción, precio y botones para agregar productos al carrito de compras o a favoritos.

Además, se implementa el concepto de programación orientada a objetos, creando un componente personalizado que hereda de una clase base de Flet. También se muestra el uso de recursos locales (assets) para cargar imágenes dentro de la aplicación.

Este proyecto demuestra cómo organizar una interfaz gráfica usando componentes reutilizables, manejo de eventos y estructuras de datos dentro del framework Flet.

# Pasos
## Ejecución del Proyecto
1. Crear entorno virtual (opcional)
python -m venv venv

2. Activar entorno
Windows:

`venv\Scripts\activate`

Mac/Linux:

`source venv/bin/activate`

3. Instalar Flet
`pip install flet`

4. Ejecutar aplicación
Catalogo_web.py


1. Datos de productos

En esta parte se define una lista de diccionarios que contiene la información de cada producto.

`productos = [
    {"nombre": "Laptop Gamer", "descripcion": "Laptop potente para juegos y diseño", "precio": 25000, "imagen": "laptop.png"},
]`

Cada producto contiene:

- nombre → nombre del producto
- descripcion → breve explicación del producto
- precio → costo del producto
- imagen → nombre de la imagen ubicada en la carpeta assets

Esta lista funciona como una base de datos simple para generar los componentes de la interfaz.

2. Clase ProductoCard
Se creó una clase llamada ProductoCard, que representa visualmente cada producto.

`class ProductoCard(ft.Container):`

Esta clase hereda de Container de Flet, lo que permite crear un componente visual personalizado.
Cada tarjeta contiene:

- Imagen del producto
- Nombre
- Descripción
- Precio
- Botón de favoritos
- Botón de agregar al carrito
<img width="564" height="409" alt="{CDE8562C-14C5-49E1-A30B-A4FE6A9A5009}" src="https://github.com/user-attachments/assets/9196460a-b21e-4217-85f1-456fa1f1531a" />

El contenido se organiza usando:

Column
Row
Image
Text
Button

Esto permite construir la tarjeta de manera estructurada.

3. Botón de Favoritos
Se utiliza un IconButton para marcar productos como favoritos.

`self.icono_fav = ft.IconButton(
    icon=ft.Icons.FAVORITE_BORDER,
    icon_color="red",
    on_click=self.toggle_favorito
)`

Cuando el usuario presiona el botón:
- Cambia el icono
- Se agrega el producto a la lista de favoritos
- Se actualiza el contador

4. Función toggle_favorito
Esta función cambia el icono del botón.
`
def toggle_favorito(self, e):`

Si el icono está vacío:

*FAVORITE_BORDER*

Se cambia a:

*FAVORITE*

Esto indica que el producto fue marcado como favorito.

5. Interfaz principal
La función principal de la aplicación es:
`
def main(page: ft.Page):`

Aquí se configura:
- título de la aplicación
- color de fondo
- scroll automático

También se crean dos listas:
'
carrito = []
favoritos = []'

Estas listas almacenan los productos seleccionados.

6. Funciones del carrito y favoritos
Se crearon funciones para actualizar los contadores.

Agregar al carrito:
`
def agregar_carrito(producto):
`
Agregar a favoritos:
`
def agregar_favorito(producto):
`
Cada vez que se agrega un producto:
- se guarda en la lista
- se actualiza el contador
- se refresca la interfaz
<img width="423" height="419" alt="{E2BF4D61-0E74-4E7D-BE1C-3AAE98AE258D}" src="https://github.com/user-attachments/assets/c0ea1067-041e-4495-9584-f2c7c3ebb5c6" />

<img width="131" height="62" alt="{C4A5CE04-706C-49F7-816D-CF73E7E5F681}" src="https://github.com/user-attachments/assets/cca06de4-3871-4e63-9273-5dac720b9df1" />

7. Generación automática de tarjetas
Las tarjetas se generan automáticamente con un ciclo.
`
for producto in productos:
    cards.append(
        ProductoCard(producto, agregar_carrito, agregar_favorito)
    )
`
Esto permite repetir el mismo componente para cada producto.
<img width="248" height="103" alt="{0C7BA753-96C3-45BE-951B-A7ACF0973FB0}" src="https://github.com/user-attachments/assets/8db401b1-9c13-492a-92ba-a49f6b057132" />

## Diagrama de clase
           +-------------------+
           |       Page        |
           |   (Aplicación)    |
           +---------+---------+
                     |
                     |
                     v
             +---------------+
             | ProductoCard  |
             | (Container)   |
             +---------------+
             | producto      |
             | icono_fav     |
             +---------------+
             | toggle_favorito() |
             +---------------+

Relación:

ProductoCard hereda de Container
main() crea múltiples instancias de ProductoCard

## Explicación de la Herencia
En este proyecto se utiliza herencia para crear un componente reutilizable.
La clase:
`
ProductoCard`
hereda de:
`
ft.Container`

Esto permite:
- reutilizar propiedades de Flet
- agregar nuevas funcionalidades
- crear componentes personalizados

Gracias a esto, cada producto puede mostrarse como una tarjeta independiente dentro de la interfaz.

## Gestión de Recursos (Assets)

Las imágenes se guardan en una carpeta llamada:
*assets*
<img width="850" height="307" alt="{00873A04-3045-4ED3-8AA5-7F82A6CE7161}" src="https://github.com/user-attachments/assets/cddfb299-b6a8-4f8c-a3e9-e5d3b08a2c7b" />

Ejemplo:

**assets/laptop.png
assets/phone.png** 
<img width="868" height="302" alt="{A3DF38E1-D42F-46A6-8B9F-7463574DB65C}" src="https://github.com/user-attachments/assets/109484cf-3164-4fe1-895c-34419d4f5106" />

En Flet se indica la carpeta de recursos con:
`
ft.app(target=main, assets_dir="assets")`

Esto permite que las imágenes se carguen usando:
`
ft.Image(src="/laptop.png")`

Flet buscará automáticamente el archivo dentro de la carpeta assets.
# Pagina web 

## Abrir en Replit 
# Pasos para subir el proyecto a Replit y sincronizar con GitHub

<img width="712" height="299" alt="image" src="https://github.com/user-attachments/assets/30053a5a-38b1-4764-9c94-ac5e838781a3" />

### Configuración inicial en Replit
`Iniciar un nuevo proyecto o importar el existente en Replit`  

Crea un workspace vacío en Replit o importa los archivos del proyecto si ya los tienes en tu equipo (mediante carga directa o vinculación con GitHub).


`Agregar archivo requirements.txt`  
`Escribir dentro: flet`  

Define la dependencia principal del proyecto (Flet), para que Replit instale automáticamente lo necesario al ejecutar el código.


### Conectar Replit con GitHub
`Ir a la pestaña "Version Control" (icono de rama de árbol) en el panel izquierdo`  

Accede a las herramientas de control de versiones integradas en Replit para gestionar el repositorio.


`Hacer clic en "Connect GitHub" y autorizar la integración`  

Vincula tu cuenta de Replit con la de GitHub para permitir la sincronización entre plataformas.


`Clic en "Initialize Repository"`  

Crea un repositorio local en el workspace de Replit, habilitando el seguimiento de cambios con Git.


### Configurar el repositorio remoto de GitHub
`Crear un repositorio nuevo en GitHub (puedes dejarlo vacío o agregar README/.gitignore/licencia)`  

Prepara el espacio en GitHub donde se almacenará el proyecto.


`Copiar la URL del repositorio GitHub (ejemplo: https://github.com/24680052/tiendatec.git`  
<img width="877" height="519" alt="image" src="https://github.com/user-attachments/assets/9da89534-0d48-4426-a8c6-fcc5267d4217" />

Obtén la dirección para vincular el repositorio local de Replit con el remoto de GitHub.


`En la terminal de Replit, ejecutar los comandos:`  
`git remote add origin https://github.com/24680052/tiendatec.git`  
`git branch -M main`  

Establece la conexión con el repositorio remoto y define la rama principal (ajusta a "master" si es tu caso).


### Subir los archivos al repositorio
`En la terminal de Replit, ejecutar secuencialmente:`  
`git add .`  
`git commit -m "Subida inicial del proyecto Flet a Replit y GitHub"`  
`git push -u origin main`  

- `git add .`: Agrega todos los archivos del proyecto al seguimiento de Git.  
- `git commit -m "...":` Registra los cambios con un mensaje descriptivo.  
- `git push ...`: Sube los archivos al repositorio de GitHub.


### Verificación final
`Ingresar al repositorio en GitHub y revisar que todos los archivos aparezcan correctamente` 

### Elegir la opcion de `Import design`
y una ves dentro de esa parte, elegir `Gitgub`
<img width="259" height="264" alt="image" src="https://github.com/user-attachments/assets/bcd4b28e-4fa4-4f40-8c43-f43b039661c5" />
### Pegar tu URL 
<img width="637" height="646" alt="image" src="https://github.com/user-attachments/assets/af796f4f-6437-4fa2-a868-300b33b088b1" />
Y daras click en `Import` 


Confirma que la sincronización se realizó exitosamente y que todos los elementos del proyecto están disponibles.


`En Replit, probar ejecutar el proyecto con el botón "Run"`  

Asegúrate de que el código funcione sin errores en el entorno de Replit, aprovechando la dependencia instalada desde `requirements.txt`.

### Asi es como se muestra dado de alta en pagina web
<img width="1140" height="788" alt="image" src="https://github.com/user-attachments/assets/dc14e8a6-c0a2-4a0f-b45e-cd69a4bb044a" />


### En esta imagen es para que si quieres compartir la pagina web tienes que seleccionar en


- Y se abrira lo siguiente



- Ya solo seleccionas si quieres pasar link o QR que te proporciona
- Una vez realizado eso lo puedes poner en algun navegador y tiene que cargar la pagina

 <img width="504" height="351" alt="image" src="https://github.com/user-attachments/assets/9b432bf6-56d1-415c-98fa-72bc478575b3" />


# Codigo Completo

    
     `` import flet as ft

    productos = [
    {"nombre": "Laptop Gamer", "descripcion": "Laptop potente para juegos y diseño", "precio": 25000, "imagen": "laptop.png"},
    {"nombre": "Smartphone", "descripcion": "Teléfono con cámara de alta resolución", "precio": 12000, "imagen": "phone.png"},
    {"nombre": "Audífonos Bluetooth", "descripcion": "Sonido envolvente inalámbrico", "precio": 1800, "imagen": "audifonos.png"},
    {"nombre": "Smartwatch", "descripcion": "Reloj inteligente con monitor de salud", "precio": 3500, "imagen": "watch.png"},
    {"nombre": "Tablet", "descripcion": "Pantalla grande ideal para estudio", "precio": 8000, "imagen": "tablet.png"}
    ]

    class ProductoCard(ft.Container):

    def __init__(self, producto, agregar_carrito, agregar_favorito):
        super().__init__()

        self.producto = producto
        self.agregar_favorito = agregar_favorito

        self.width = 260
        self.padding = 15
        self.border_radius = 15
        self.bgcolor = "white"

        self.shadow = ft.BoxShadow(
            blur_radius=15,
            offset=ft.Offset(4,4),
            color=ft.Colors.BLACK12
        )

        self.icono_fav = ft.IconButton(
            icon=ft.Icons.FAVORITE_BORDER,
            icon_color="red",
            on_click=self.toggle_favorito
        )

        self.content = ft.Column(
            horizontal_alignment=ft.CrossAxisAlignment.CENTER,
            controls=[

                ft.Image(
                    src=f"/{producto['imagen']}",
                    width=120,
                    height=120
                ),

                ft.Text(
                    producto["nombre"],
                    size=18,
                    weight=ft.FontWeight.BOLD
                ),

                ft.Text(
                    producto["descripcion"],
                    size=12,
                    text_align=ft.TextAlign.CENTER
                ),

                ft.Text(
                    f"${producto['precio']}",
                    size=16,
                    color=ft.Colors.GREEN,
                    weight=ft.FontWeight.BOLD
                ),

                ft.Row(
                    alignment=ft.MainAxisAlignment.CENTER,
                    controls=[
                        self.icono_fav
                    ]
                ),

                ft.ElevatedButton(
                    "Agregar al carrito",
                    icon=ft.Icons.SHOPPING_CART,
                    on_click=lambda e: agregar_carrito(self.producto)
                )

            ]
        )

    def toggle_favorito(self, e):

        if self.icono_fav.icon == ft.Icons.FAVORITE_BORDER:
            self.icono_fav.icon = ft.Icons.FAVORITE
            self.agregar_favorito(self.producto)
        else:
            self.icono_fav.icon = ft.Icons.FAVORITE_BORDER

        self.update()

    def main(page: ft.Page):

    page.title = "Tienda Tecnológica"
    page.bgcolor = "#f2f2f2"
    page.scroll = "auto"

    carrito = []
    favoritos = []

    contador_carrito = ft.Text("0")
    contador_fav = ft.Text("0")

    # -----------------------
    # FUNCIONES
    # -----------------------

    def agregar_carrito(producto):
        carrito.append(producto)
        contador_carrito.value = str(len(carrito))
        page.update()

    def agregar_favorito(producto):
        favoritos.append(producto)
        contador_fav.value = str(len(favoritos))
        page.update()

    # -----------------------
    # CREAR TARJETAS
    # -----------------------

    cards = []

    for producto in productos:
        cards.append(
            ProductoCard(producto, agregar_carrito, agregar_favorito)
        )

    # -----------------------
    # INTERFAZ
    # -----------------------

    page.add(

        ft.Column(
            controls=[

                ft.Row(
                    alignment=ft.MainAxisAlignment.SPACE_BETWEEN,
                    controls=[

                        ft.Text(
                            "Tienda Tecnológica",
                            size=30,
                            weight=ft.FontWeight.BOLD
                        ),

                        ft.Row(
                            controls=[

                                ft.Icon(ft.Icons.FAVORITE, color="red"),
                                contador_fav,

                                ft.Icon(ft.Icons.SHOPPING_CART),
                                contador_carrito

                            ]
                        )

                    ]
                ),

                ft.Row(
                    controls=cards,
                    wrap=True,
                    spacing=20
                )

            ]
        )

    )

    ft.app(target=main, assets_dir="assets")
``
# Ejecucion del codigo
<img width="1119" height="678" alt="{F326041D-A645-454E-9819-D3EE580950C8}" src="https://github.com/user-attachments/assets/ad1e359f-dac6-4789-9c86-7b94ecf606c5" />

# Conlusion

Este proyecto demuestra cómo desarrollar una aplicación gráfica utilizando Python y Flet, aplicando conceptos de programación orientada a objetos, reutilización de componentes y manejo de eventos.

El uso de una clase personalizada permite crear tarjetas de productos reutilizables, mientras que la gestión de recursos mediante la carpeta assets facilita la integración de imágenes dentro de la interfaz.

Además, la generación dinámica de componentes a partir de una estructura de datos permite construir interfaces escalables y fáciles de mantener.

