## Acerca del Proyecto
### Objetivo
<p>Aplicar los conocimientos adquiridos en clases del lenguaje de programacion Python </p>

### Descripcion del Caso
<p>
Empresa con varias cuatro sucursales en el pais de Colombia, que ofrece informacion de las operaciones de cada tienda, el dueño requiere tomar conocimiento acerca de la produccion operativa de cada tienda (ingresos, costos, nivel de satisfaccion del cliente, categorias y productos mas vendidos), la informacion debe permitir realizar un analisis para selccionar la tienda que debe ser vendida por baja producción 
</p>

## Ambiente de Desarrollo
- Github : Control de versiones
- Google Collab : Editor de Python
- Matplotlib.pyplot, plotly.express  para generacion de Graficos

## Carga de Datos
**Clonamos repositorio de Datos de Github en Drive**
git clone https://github.com/alura-es-cursos/challenge1-data-science-latam.git

## Desarrollo de Consultas
### A. Calculo de Facturacion
**Funcion de Calculo de Ingresos (tienda)**
+ **input:**
  + Tienda = direccion de file ('/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
+ **calculo**
  + Importa archivo
-- suma = data['Precio'].sum()
+ **output**
  + ingresos totales

**Programa principal, invoca a funcion y obtiene ingresos**
+ **Ciclos de Ejecucion**
  + ciclos(4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
  + resultado = calculo_ingresos(tienda)
+ **Resultado Final**
  + Ingresos por Tienda

### B.  Catidad de Ventas por Categoria
**Funcion de categoria_frecuencia (tienda)**
+ **input:**
  + tienda = direccion de file(/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
+ **Calculo**
  + frecuencias = df['Categoría del Producto'].value_counts().head(5)
  + frecuencias_df = frecuencias.reset_index()
  + frecuencias_df.columns = ['Categoría del Producto', 'Cantidad']
+ **Output**
  + Totales por Categoria

**Programa principal, invoca a funcion y obtiene Totales por Categoria**
+ **Ciclos de Ejecucion**
  + Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
  + resultado = categoria_frecuencia(tienda)
  **Resultado Final**
  + Conteo de Ventas por Categoria por Tienda

### C. Promedio de Calificacion
**Funcion de calculo_calificacion (tienda)**
+ **input:**
  + tienda = direccion de file (/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
 + **Calculo**
  + promedio_calificacion = df['Calificación'].mean()
 + **Output**
  + Promedio de satisfaccion por tienda

**Programa principal, invoca a funcion y obtiene Promedio Calificacion**
+ **Ciclo de Ejecucion**
  + Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
  + resultado = round(calculo_calificacion(tienda),2)
+ **Resultado**
  + Satisfaccion Promedio  por tienda

### D. Productos Mas y Menos Vendidos  por Tienda
**Funcion de frecuencia_productos (tienda)**
+ **input:**
  + tienda = direccion de file (/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
  + Opcion = 1:Maximos  2: Minimos
+ **Calculo**
  + if opcion == 1:
    + frecuencias_prod_max = df['Producto'].value_counts().head(3)
    + frecuencias_df_prod = frecuencias_prod_max.reset_index()
  + else:
    + frecuencias_prod_min = df['Producto'].value_counts().tail(3)
    + frecuencias_df_prod = frecuencias_prod_min.reset_index()
+ **Output**
  + Promedio de calificacion

**Programa principal, invoca a funcion y obtiene Totales por Categoria**
+ **Ciclo de Ejecucion**
  + Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
  + resultado = conteo_ventas(tienda,opcion)
+ **Resultado Final**
  + Ranking de Productos mas vendidos(3)
  + Ranking de Productos menos vendidos(3)
  

### E. Promedio de Costo de Envio  por Tienda
**Funcion de calculo_envio (tienda)**
+ **input:**
  + tienda = direccion de file (/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
 + **Calculo**
  + promedio_envio = df['Costo de envío'].mean()
+ **Output**
  + Total de Costo de Envio por tienda

**Programa principal, invoca a funcion y obtiene Totales por Categoria**
+ **Ciclo de Ejecucion**
  + Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
  + resultado = round(calculo_envio(tienda),2)
+ **Resultado Final**
  + Total de Costo de Envio por tienda

### F. Graficos
**Grafico de Barras Verticales - Distribucion de  Ingresos**
+ **input:**
  + Resultado de A. Calculo de Ingresos
+ **Calculo**
  + df = pd.DataFrame(dict(grupo = ["Tienda 1","Tienda 2", "Tienda 3","Tienda 4"], valor = list(resumen_ingreso)))
  + fig = px.bar(df, x = 'grupo', y = 'valor',title = "Distribucion de Ingresos por Tienda",labels = {'grupo': 'Tiendas', 'valor': 'Ingresos'})
+ **Output**
  + Grafico de Distribucion de Ingresos por Tiendas

**Grafico de Barras Horizontales Distribucion Promedio de Satisfaccion**
+ **input:**
  + Resultado de C. Promedio de Calificacion
+ **Calculo**
  + df = pd.DataFrame(dict(Tiendas = ["Tienda 1","Tienda 2", "Tienda 3","Tienda 4"],Satisfaccion = list(promedio_satisfaccion)))
  + fig = px.bar(df, x = 'Satisfaccion', y = 'Tiendas',pattern_shape = 'Tiendas', text_auto = True)
+ **Output**
  + Grafico de Distribucion Promedio de Satisfaccion

**Grafico Pie  Distribucion Venta por Categorias de Tienda 1**
+ **input:**
  + Resultado de D. Ranking de Categorias Tienda 1
+ **Calculo**
  + import matplotlib.pyplot as plt
  + plt.figure(figsize=(10, 8))
  + categoria = lista_categorias
  + unidades = lista_ventas
  + destacar = [0.1,0,0,0,0,0,0,0]
  + plt.style.use("ggplot")
  + plt.title("Distribucion de ventas por Categorias Tienda 1")
  + plt.pie(x=unidades,explode=destacar,labels=categoria,autopct='%.2f%%',shadow=True,startangle=20)
  + plt.axis('equal')
  + plt.legend(loc="upper left")
+ **Output**
  + Grafico de Distribucion cantidad de ventas por categorias Tienda 1
