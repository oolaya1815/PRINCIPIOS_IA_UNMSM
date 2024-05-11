# Vivienda en California

## Fuente
Este conjunto de datos es una versión modificada del conjunto de datos de Vivienda en California disponible en la página de Luís Torgo (Universidad de Oporto). Luís Torgo lo obtuvo del repositorio StatLib (que ahora está cerrado). El conjunto de datos también se puede descargar de los espejos de StatLib.

Este conjunto de datos apareció en un artículo de 1997 titulado *Sparse Spatial Autoregressions* por Pace, R. Kelley y Ronald Barry, publicado en la revista *Statistics and Probability Letters*. Lo construyeron utilizando los datos del censo de California de 1990. Contiene una fila por grupo de bloques del censo. Un grupo de bloques es la unidad geográfica más pequeña para la cual la Oficina del Censo de los EE. UU. publica datos de muestra (un grupo de bloques típicamente tiene una población de 600 a 3,000 personas).

## Modificaciones
El conjunto de datos en este directorio es casi idéntico al original, con dos diferencias:

* Se eliminaron aleatoriamente 207 valores de la columna `total_bedrooms`, para que podamos discutir qué hacer con los datos faltantes.
* Se agregó un atributo categórico adicional llamado `ocean_proximity`, que indica (muy aproximadamente) si cada grupo de bloques está cerca del océano, cerca del área de la Bahía, en el interior o en una isla. Esto permite discutir qué hacer con los datos categóricos.

Tenga en cuenta que los grupos de bloques se llaman "distritos" en los cuadernos Jupyter, simplemente porque en algunos contextos el nombre "grupo de bloques" era confuso.

## Descripción de los datos

    >>> housing.info()
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20640 entries, 0 to 20639
    Data columns (total 10 columns):
    longitude             20640 non-null float64
    latitude              20640 non-null float64
    housing_median_age    20640 non-null float64
    total_rooms           20640 non-null float64
    total_bedrooms        20433 non-null float64
    population            20640 non-null float64
    households            20640 non-null float64
    median_income         20640 non-null float64
    median_house_value    20640 non-null float64
    ocean_proximity       20640 non-null object
    dtypes: float64(9), object(1)
    memory usage: 1.6+ MB
    
    >>> housing["ocean_proximity"].value_counts()
    <1H OCEAN     9136
    INLAND        6551
    NEAR OCEAN    2658
    NEAR BAY      2290
    ISLAND           5
    Name: ocean_proximity, dtype: int64
    
    >>> housing.describe()
              longitude      latitude  housing_median_age   total_rooms  \
    count  16513.000000  16513.000000        16513.000000  16513.000000   
    mean    -119.575972     35.639693           28.652335   2622.347605   
    std        2.002048      2.138279           12.576306   2138.559393   
    min     -124.350000     32.540000            1.000000      6.000000   
    25%     -121.800000     33.940000           18.000000   1442.000000   
    50%     -118.510000     34.260000           29.000000   2119.000000   
    75%     -118.010000     37.720000           37.000000   3141.000000   
    max     -114.310000     41.950000           52.000000  39320.000000   

           total_bedrooms    population    households  median_income  
    count    16355.000000  16513.000000  16513.000000   16513.000000  
    mean       534.885112   1419.525465    496.975050       3.875651  
    std        412.716467   1115.715084    375.737945       1.905088  
    min          2.000000      3.000000      2.000000       0.499900  
    25%        295.000000    784.000000    278.000000       2.566800  
    50%        433.000000   1164.000000    408.000000       3.541400  
    75%        644.000000   1718.000000    602.000000       4.745000  
    max       6210.000000  35682.000000   5358.000000      15.000100
 
