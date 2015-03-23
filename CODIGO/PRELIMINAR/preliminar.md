Analisis de datos
========================================================






```r
directorio <- "C:\\Users\\Patatas\\Desktop\\ea1-pr"
setwd(directorio)
```



### Librerias utilizadas

```r
paquetes.utilizados <- c("reshape2", "tidyr", "xtable", "knitr", "qdap",
                         "dplyr", "plyr", "lubridate", "ggplot2", "openxlsx")
paquetes.instalados <- rownames(installed.packages())
paquetes.por.instalar <- setdiff(paquetes.utilizados, paquetes.instalados)

# Instala los paquetes faltantes.
if (length(paquetes.por.instalar) != 0 ) install.packages(paquetes.por.instalar, 
                                                          repos = "http://cran.us.r-project.org")
```

```
## Installing package into 'C:/Users/Patatas/Documents/R/win-library/3.0'
## (as 'lib' is unspecified)
```

```
## Warning: package 'tidyr' is not available (for R version 3.0.2)
```

```r
# Carga los paquetes a utilizar.
lapply(paquetes.utilizados, library, character.only = TRUE)
```

```
## Warning: package 'reshape2' was built under R version 3.0.3
```

```
## Error in FUN(c("reshape2", "tidyr", "xtable", "knitr", "qdap", "dplyr", : there is no package called 'tidyr'
```



```r
setwd("./DATOS/BRUTOS/csv")
```

```
## Error in setwd("./DATOS/BRUTOS/csv"): cannot change working directory
```

```r
nombres <- list.files(pattern= "*.csv")
for (i in 1:length(nombres)){
  assign( substr(nombres[i], 1, nchar(nombres[i])-4), read.csv(nombres[i]))
}
```

```
## Warning in file(file, "rt"): cannot open file 'NA': No such file or
## directory
```

```
## Error in file(file, "rt"): cannot open the connection
```


```r
nombres_sin <- nombres
for (i in 1:length(nombres)){
  nombres_sin[i] <- substr(nombres[i], 1, nchar(nombres[i])-4)
}
```


```r
for (i in 1:33){
  assign(nombres_sin[i], melt (data = read.csv(nombres[i]), na.rm=TRUE, variable.name ="fuente", value.name= "numero", id =1))
  
}
```

```
## Warning in file(file, "rt"): cannot open file 'NA': No such file or
## directory
```

```
## Error in file(file, "rt"): cannot open the connection
```






