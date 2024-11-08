## TAREA 12


## Ejercicio 1: Generación de la Distribución Normal en Python

Usa la función numpy.random.normal en Python para generar una muestra de 1000 valores que siguen una distribución normal con media = 60 y desviación estándar = 15.
Genera un histograma de esta muestra y observa su forma.
Calcula la media y la desviación estándar de la muestra generada.


    import numpy as np
    import matplotlib.pyplot as plt

    muestra = np.random.normal(60, 15, 1000)

    media_muestra = np.mean(muestra)
    desviacion_muestra = np.std(muestra)

    print("Media de la muestra:", media_muestra)
    print("Desviación estándar de la muestra:", desviacion_muestra)

    plt.hist(muestra, bins=30, color='skyblue', edgecolor='black')
    plt.title("Histograma de la muestra con distribución normal")
    plt.xlabel("Valores")
    plt.ylabel("Frecuencia")
    plt.show()

![image](https://github.com/user-attachments/assets/236023f1-41f0-421c-9ecd-5fd9b5bcc210)


## Ejercicio 2: Probabilidad en un Rango Específico en R

Usando una distribución normal con media = 40 y desviación estándar = 5, calcula la probabilidad de que un valor esté entre 35 y 45.
Usa la función pnorm en R para realizar este cálculo.


    media <- 40
    desviacion <- 5

    prob_45 <- pnorm(45, mean = media, sd = desviacion)
    prob_35 <- pnorm(35, mean = media, sd = desviacion)
    probabilidad <- prob_45 - prob_35
    cat("La probabilidad de que un valor esté entre 35 y 45 es:", probabilidad, "\n")

![image](https://github.com/user-attachments/assets/63607a4f-7c5a-4585-b858-464f5aefef33)

### con Historagrama 


    library(ggplot2)

    media <- 40
    desviacion <- 5

    prob_45 <- pnorm(45, mean = media, sd = desviacion)
    prob_35 <- pnorm(35, mean = media, sd = desviacion)  
    probabilidad <- prob_45 - prob_35

    cat("La probabilidad de que un valor esté entre 35 y 45 es:", probabilidad, "\n")

    set.seed(123)
    muestra <- rnorm(1000, mean = media, sd = desviacion)

    ggplot(data.frame(muestra), aes(x = muestra)) +
      geom_histogram(aes(y = ..density..), bins = 30, fill = "skyblue", color = "black", alpha = 0.7) +
      stat_function(fun = dnorm, args = list(mean = media, sd = desviacion), color = "red", size = 1) +
      geom_area(stat = "function", fun = dnorm, args = list(mean = media, sd = desviacion),
                xlim = c(35, 45), fill = "orange", alpha = 0.3) +
      labs(title = "Distribución Normal con Media 40 y Desviación Estándar 5",
               x = "Valores", y = "Densidad") +
      annotate("text", x = 40, y = 0.05, label = paste("Probabilidad entre 35 y 45:", round(probabilidad, 4)),
               color = "black", size = 4, vjust = -1) +
      theme_minimal()
![image](https://github.com/user-attachments/assets/10f68191-cd00-4d55-8de5-19f115d4d0a3)

## Ejercicio 3: Simulación de una Muestra en Python

Genera una muestra de 500 observaciones que sigan una distribución normal con media = 75 y desviación estándar = 8.
Calcula el intervalo de confianza al 95% para la media de la muestra.
Grafica la muestra y marca los límites del intervalo de confianza.


    import numpy as np
    import scipy.stats as stats
    import matplotlib.pyplot as plt

    muestra = np.random.normal(75, 8, 500)

    media_muestra = np.mean(muestra)
    error_estandar = stats.sem(muestra)

    intervalo_confianza = stats.norm.interval(0.95, loc=media_muestra, scale=error_estandar)
    limite_inferior, limite_superior = intervalo_confianza

    print("Media de la muestra:", media_muestra)
    print("Intervalo de confianza al 95%:", intervalo_confianza)

    plt.hist(muestra, bins=30, color='lightblue', edgecolor='black', alpha=0.7, density=True)
    plt.axvline(media_muestra, color='blue', linestyle='dashed', linewidth=2, label='Media de la muestra')
    plt.axvline(limite_inferior, color='red', linestyle='dashed', linewidth=2, label='Límite inferior (95%)')
    plt.axvline(limite_superior, color='green', linestyle='dashed', linewidth=2, label='Límite superior (95%)')

    plt.title("Histograma de la muestra con Intervalo de Confianza al 95%")
    plt.xlabel("Valores")
    plt.ylabel("Frecuencia")
    plt.legend()
    plt.show()

![image](https://github.com/user-attachments/assets/01fecd23-c6db-450f-ab2a-a415f7d6c4e9)

## Ejercicio 4: Comparación de dos Distribuciones en R

Genera dos muestras de 1000 valores cada una:
Muestra A con media = 55 y desviación estándar = 10
Muestra B con media = 65 y desviación estándar = 15
Grafica ambas distribuciones en el mismo histograma para compararlas.
Compara la media y la desviación estándar de cada muestra.


    set.seed(123) 
    muestra_a <- rnorm(1000, mean = 55, sd = 10)  
    muestra_b <- rnorm(1000, mean = 65, sd = 15)  

    xlim_range <- range(c(muestra_a, muestra_b))

    hist(muestra_a, col=rgb(1,0,0,0.5), xlim=xlim_range, 
         main="Comparación de Distribuciones", xlab="Valor", ylab="Frecuencia", 
         breaks=30, freq=FALSE)

    hist(muestra_b, col=rgb(0,0,1,0.5), add=TRUE, breaks=30, freq=FALSE)
    legend("topright", legend=c("Muestra A", "Muestra B"), fill=c(rgb(1,0,0,0.5), rgb(0,0,1,0.5)))

    media_a <- mean(muestra_a)
    sd_a <- sd(muestra_a)

    media_b <- mean(muestra_b)
    sd_b <- sd(muestra_b)

    cat("Muestra A - Media:", media_a, "Desviación estándar:", sd_a, "\n")
    cat("Muestra B - Media:", media_b, "Desviación estándar:", sd_b, "\n")

  ![image](https://github.com/user-attachments/assets/306621ee-0d60-4a9f-9125-996e19800450)

 ![image](https://github.com/user-attachments/assets/7d44f2e2-9e25-43cc-bab7-972f5ca3c7c9)


## Ejercicio 5: Cálculo de Percentiles en Python

Genera una muestra de 100 valores con media = 100 y desviación estándar = 20.
Calcula el percentil 90 de esta muestra.
Interpreta el resultado en el contexto de la muestra.

    import numpy as np

    muestra = np.random.normal(100, 20, 100)
    percentil_90 = np.percentile(muestra, 90)
    print("Percentil 90 de la muestra:", percentil_90)

 ![image](https://github.com/user-attachments/assets/f5ddf694-e732-4de7-ad21-8b52de2a1b19)

### Histograma 

    import numpy as np
    import matplotlib.pyplot as plt

    muestra = np.random.normal(100, 20, 100)
    percentil_90 = np.percentile(muestra, 90)
    print("Percentil 90 de la muestra:", percentil_90)
    plt.hist(muestra, bins=30, color='skyblue', edgecolor='black')
    plt.axvline(percentil_90, color='red', linestyle='dashed', linewidth=1.5, label=f'Percentil 90: {percentil_90:.2f}')
    plt.title("Histograma de la muestra con distribución normal")
    plt.xlabel("Valores")
    plt.ylabel("Frecuencia")
    plt.legend()
    plt.show()
![image](https://github.com/user-attachments/assets/6d7f714a-9944-4f4c-b339-2443ca23acd7)

## Ejercicio 6: Probabilidad de Exceder un Valor en R

En una distribución normal con media = 50 y desviación estándar = 12, calcula la probabilidad de que un valor sea mayor que 70.
Usa pnorm en R para resolverlo.

    media <- 50
    desviacion <- 12

    probabilidad <- 1 - pnorm(70, mean = media, sd = desviacion)
    cat("La probabilidad de que un valor sea mayor que 70 es:", probabilidad, "\n")
![image](https://github.com/user-attachments/assets/076bb451-7e54-4e72-a58a-9b0552e75239)
### Histograma 

    library(ggplot2)

    media <- 50
    desviacion <- 12
    probabilidad <- 1 - pnorm(70, mean = media, sd = desviacion)
    cat("La probabilidad de que un valor sea mayor que 70 es:", probabilidad, "\n")

    set.seed(123)
    muestra <- rnorm(1000, mean = media, sd = desviacion)
    ggplot(data.frame(muestra), aes(x = muestra)) +
      geom_histogram(aes(y = ..density..), bins = 30, fill = "skyblue", color = "black", alpha = 0.7) +
      stat_function(fun = dnorm, args = list(mean = media, sd = desviacion), color = "red", size = 1) +
      geom_area(stat = "function", fun = dnorm, args = list(mean = media, sd = desviacion),
                xlim = c(70, Inf), fill = "orange", alpha = 0.3) +
      labs(title = "Distribución Normal con Media 50 y Desviación Estándar 12",
           x = "Valores", y = "Densidad") +
      annotate("text", x = 80, y = 0.02, label = paste("Probabilidad > 70:", round(probabilidad, 4)),
               color = "black", size = 4, vjust = -1) +
      theme_minimal()

  ![image](https://github.com/user-attachments/assets/34f4d289-bacf-4bd4-ba17-1c7c99d65748)

## Ejercicio 7: Simulación de Distribución Normal Estándar en Python

Genera una muestra de 1000 valores de una distribución normal estándar (media = 0 y desviación estándar = 1).
Calcula el porcentaje de valores entre -1 y 1.
Comprueba si el porcentaje es aproximadamente 68%.

    import numpy as np
    muestra = np.random.normal(0, 1, 1000)

    valores_entre = np.sum((muestra >= -1) & (muestra <= 1))
    porcentaje = (valores_entre / len(muestra)) * 100
    print("Porcentaje de valores entre -1 y 1:", porcentaje, "%")

  ![image](https://github.com/user-attachments/assets/208932fd-d69b-4840-a163-e85a0420a558)

### Histograma 

    import numpy as np
    import matplotlib.pyplot as plt

    muestra = np.random.normal(0, 1, 1000)

    valores_entre = np.sum((muestra >= -1) & (muestra <= 1))
    porcentaje = (valores_entre / len(muestra)) * 100
    print("Porcentaje de valores entre -1 y 1:", porcentaje, "%")
    plt.hist(muestra, bins=30, color='skyblue', edgecolor='black', alpha=0.7)
    plt.axvspan(-1, 1, color='orange', alpha=0.3, label=f"Valores entre -1 y 1: {porcentaje:.2f}%")

    plt.title("Histograma de la muestra con distribución normal")
    plt.xlabel("Valores")
    plt.ylabel("Frecuencia")
    plt.legend()
    plt.show()

![image](https://github.com/user-attachments/assets/27e987b4-abd4-404a-84c9-37ab668ac457)

## Ejercicio 8: Prueba de Normalidad en R

Genera una muestra de 200 valores con media = 30 y desviación estándar = 5.
Realiza una prueba de normalidad en la muestra usando shapiro.test en R.

    set.seed(123) 
    muestra <- rnorm(200, mean = 30, sd = 5)

    prueba_normalidad <- shapiro.test(muestra)
    cat("Resultado de la prueba de normalidad (Shapiro-Wilk):\n")
    print(prueba_normalidad)

![image](https://github.com/user-attachments/assets/a67b2a47-b984-4789-9916-3dd0c45d4905)

### Histograma 

    library(ggplot2)

    set.seed(123)
    muestra <- rnorm(200, mean = 30, sd = 5)
    prueba_normalidad <- shapiro.test(muestra)

    cat("Resultado de la prueba de normalidad (Shapiro-Wilk):\n")
    print(prueba_normalidad)

    ggplot(data.frame(muestra), aes(x = muestra)) +
      geom_histogram(aes(y = ..density..), bins = 20, fill = "skyblue", color = "black", alpha = 0.7) +
      stat_function(fun = dnorm, args = list(mean = mean(muestra), sd = sd(muestra)), color = "red", size = 1) +
      labs(title = "Histograma de la muestra y curva de densidad normal",
           subtitle = paste("Prueba de Shapiro-Wilk: p-value =", round(prueba_normalidad$p.value, 4)),
           x = "Valores", y = "Densidad") +
      theme_minimal()

![image](https://github.com/user-attachments/assets/df1f05d9-839e-4a28-8763-265ef540aa82)

## Ejercicio 9: Transformación de una Muestra a una Distribución Normal Estándar en Python

Genera una muestra de 150 valores con media = 60 y desviación estándar = 10.
Transforma los valores de la muestra para que tengan media 0 y desviación estándar 1.
Verifica los estadísticos de la muestra transformada.

    import numpy as np

    muestra = np.random.normal(60, 10, 150)
    muestra_transformada = (muestra - np.mean(muestra)) / np.std(muestra)
    media_transformada = np.mean(muestra_transformada)
    desviacion_transformada = np.std(muestra_transformada)

    print("Estadísticos de la muestra transformada:")
    print("  Media:", media_transformada)
    print("  Desviación estándar:", desviacion_transformada)

![image](https://github.com/user-attachments/assets/3868187d-9c35-4e88-9f03-f155954c0070)

### Histograma

![image](https://github.com/user-attachments/assets/cdde3b60-7dc4-49eb-940a-e701445408bb)

## Ejercicio 10: Análisis de la Suma de Dos Variables Normales en R

Genera dos muestras de 100 observaciones cada una:

Muestra X: media = 10 y desviación estándar = 3
Muestra Y: media = 15 y desviación estándar = 4
Suma los valores correspondientes de X y Y para crear una nueva muestra Z.
Calcula la media y la desviación estándar de Z y compáralos con los valores teóricos esperados.



    library(ggplot2)

    set.seed(123)
    X <- rnorm(100, mean = 10, sd = 3)
    Y <- rnorm(100, mean = 15, sd = 4)

    Z <- X + Y
    media_Z <- mean(Z)
    desviacion_Z <- sd(Z)

    media_teorica <- mean(X) + mean(Y)
    desviacion_teorica <- sqrt(sd(X)^2 + sd(Y)^2)

    cat("Media de Z (calculada):", media_Z, "\n")
    cat("Desviación estándar de Z (calculada):", desviacion_Z, "\n")
    cat("Media de Z (teórica):", media_teorica, "\n")
    cat("Desviación estándar de Z (teórica):", desviacion_teorica, "\n")

    ggplot(data.frame(Z), aes(x = Z)) +
      geom_histogram(aes(y = ..density..), bins = 30, fill = "skyblue", color = "black", alpha = 0.7) +
      stat_function(fun = dnorm, args = list(mean = media_Z, sd = desviacion_Z), color = "red", size = 1) +
      labs(title = "Histograma de Z = X + Y con Curva de Densidad Normal",
           subtitle = paste("Media teórica =", round(media_teorica, 2), 
                            "Desviación teórica =", round(desviacion_teorica, 2)),
           x = "Valores de Z", y = "Densidad") +
      theme_minimal()

![image](https://github.com/user-attachments/assets/8cfb9f4a-7d1f-415f-b381-7da980b5e261)


