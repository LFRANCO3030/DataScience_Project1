## Acerca del Proyecto
###Objetivo
<p>Aplicar los conocimientos adquiridos en clases del lenguaje de programacion Python </p>

### Descripcion del Caso
<p>
Empresa con varias cuatro sucursales en el pais de Colombia, que ofrece informacion de las operaciones de cada tienda, el dueño requiere tomar conocimiento acerca de la produccion operativa de cada tienda (ingresos, costos, nivel de satisfaccion del cliente, categorias y productos mas vendidos), la informacion debe permitir realizar un analisis para selccionar la tienda que debe ser vendida por baja producción 
</p>

##Ambiente de Desarrollo
- Github : Control de versiones
- Google Collab : Editor de Python
- Matplotlib.pyplot, plotly.express  para generacion de Graficos

## Carga de Datos
**Clonamos repositorio de Datos de Github en Drive**
git clone https://github.com/alura-es-cursos/challenge1-data-science-latam.git

## Desarrollo de Consultas
### A. Calculo de Facturacion
- **Funcion de Calculo de Ingresos (tienda)**
	input: 
		tienda = direccion de file ('/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
	calculo
		Importa archivo
		Lazo de sumatoria de precio
	output
			ingresos totales
- **Programa principal, invoca a funcion y obtiene ingresos**
	Ciclos de Ejecucion
		ciclos(4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
		resultado = calculo_ingresos(tienda)
	Resultado Final
		Ingresos por Tienda

### B. Ventas por Categoria
- **Funcion de Conteo_Ventas (tienda,columna_a_contar)**
	Input
		tienda = direccion de file(/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
		columna_a_contar= 1 (Categoria)
	Calculo
			Lazo de sumatoria de valores de columna 1 (Categoria)
	Output
		Totales por Categoria
- **Programa principal, invoca a funcion y obtiene Totales por Categoria**
	Ciclos de Ejecucion
		Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
		resultado = conteo_ventas(tienda,columna_a_contar)
		Sorteo de Categorias (Mayor a Menor)
		resultado_sort = dict(sorted(resultado.items(), key=lambda item: item[1], reverse = True)[:3])
	Resultado Final
		Conteo de Ventas por Categoria por Tienda

### C. Calificacion Promedio Satisfacción  por Tienda
- **Funcion de Conteo_Ventas (tienda,columna_a_contar)**
	Input
		tienda = direccion de file (/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
		columna_a_contar= 7 (Satisfaccion)
	Calculo
			Lazo 
				sumatoria de valores de columna 7 (Satisfaccion)
				Conteo de registros
			Calculo de promedio
	Output
		Promedio de satisfaccion por tienda
- **Programa principal, invoca a funcion y obtiene Totales por Categoria**
	Ciclo de Ejecucion
		Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
		resultado = round(calculo_calificacion(tienda,columna_a_sumar),2)
	Resultado
		Satisfaccion Promedio  por tienda

### D. Productos Mas y Menos Vendidos  por Tienda
- **Funcion de Conteo_Ventas (tienda,columna_a_contar)**
	Input
		tienda = direccion de file (/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
		columna_a_contar= 0 (Producto)
	Calculo
			Lazo 
				sumatoria de valores de columna 0 (Producto)
				Conteo de registros
			Calculo de conteo de registros por producto
	Output
		Promedio de satisfaccion por tienda
- **Programa principal, invoca a funcion y obtiene Totales por Categoria**
	Ciclo de Ejecucion
		Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
		resultado = conteo_ventas(tienda,columna_a_contar)
		Ranking de Productos mas vendidos(3)
			resultado_sort_max = dict(sorted(resultado.items(), key=lambda item: item[1], reverse = True)[:3])
		Ranking de Productos menos vendidos(3)
			resultado_sort_min = dict(sorted(resultado.items(), key=lambda item: item[1])[:3])
	Resultado Final
		Ranking de los 3 productos mas vendidos
		Ranking de los 3 productos menos vendidos

### E. Promedio de Costo de Envio  por Tienda
- **Funcion de calculo_envio (tienda,columna_a_sumar)**
	Input
		tienda = direccion de file (/content/challenge1-data-science-latam/base-de-datos-challenge1-latam/tienda_1 .csv)
		columna_a_contar= 3 (Costo Envio)
	Calculo
			Lazo 
				sumatoria de valores de columna 3 (Costo Envio)
	Output
		Total de Costo de Envio por tienda
- **Programa principal, invoca a funcion y obtiene Totales por Categoria**
	Ciclo de Ejecucion
		Ciclos (4) de invocacion(tienda1,tienda2,tienda3,tienda4) a la funcion
		resultado = round(calculo_envio(tienda,columna_a_sumar),2)
	Resultado Final
		Total de Costo de Envio por tienda

### F. Graficos
- **Grafico de Barras Verticales - Distribucion de  Ingresos **
	Input
		 Resultado de A. Calculo de Ingresos
	Calculo
		 df = pd.DataFrame(dict(grupo = ["Tienda 1","Tienda 2", "Tienda 3","Tienda 4"], valor = list(resumen_ingreso)))
		fig = px.bar(df, x = 'grupo', y = 'valor',
             title = "Distribucion de Ingresos por Tienda",
             labels = {'grupo': 'Tiendas', 'valor': 'Ingresos'})
	Output
		Grafico de Distribucion de Ingresos por Tiendas

- **Grafico de Barras Horizontales Distribucion Promedio de Satisfaccion**
	Input
		Resultado de C. Calculo de Ingresos
	Calculo
		df = pd.DataFrame(dict(Tiendas = ["Tienda 1","Tienda 2", "Tienda 3","Tienda 4"],Satisfaccion = list(promedio_satisfaccion)))
		fig = px.bar(df, x = 'Satisfaccion', y = 'Tiendas',pattern_shape = 'Tiendas', text_auto = True)
	Output
		Grafico de Distribucion Promedio de Satisfaccion

- **Grafico Pie  Distribucion Venta por Categorias de Tienda 1**
	Input
		Resultado de D. Ranking de Productos Mas y Menos vendidos
	Calculo
		import matplotlib.pyplot as plt
		plt.figure(figsize=(10, 8))
		categoria = lista_categorias
		unidades = lista_ventas
		destacar = [0.1,0,0,0,0,0,0,0]
		plt.style.use("ggplot")
		plt.title("Distribucion de ventas por Categorias Tienda 1")
		plt.pie(x=unidades,explode=destacar,labels=categoria,autopct='%.2f%%',shadow=True,startangle=20)
		plt.axis('equal')
		plt.legend(loc="upper left")

Output
		Grafico de Distribucion Venta por categorias Tienda 1
