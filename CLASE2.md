# DEMOGRAFIA
install.packages("dplyr")
require(dplyr)
mundo <- as_tibble(read.csv(file.choose())) #es para llamar nuestra base, es como data.frame
#%>% es el pay sirve para hacer una a una, renglon por renglon
italia <- mundo %>%
  as_tibble() %>%
  filter(iso_code== "ITA")
nicaragua <- mundo %>%
  as_tibble() %>%
  filter(iso_code== "NIC") #abrimos un filtro, es como seleccionar una columna
max(italia$total_cases) 
max(italia$new_cases)

italiamax <- mundo %>%
  as_tibble() %>%
  filter(iso_code== "ITA") %>%
mutate(acumulado=cumsum(new_cases))%>% #cumsum es suma acumulada
filter(between(acumulado,200000, 228000)) #filtrame entre 1000 y 3000 de la variable acumulada


italiamax <- mundo %>%
  as_tibble() %>%
  filter(between(new_cases,200000, 228000)) 
  table(italiamax$location)
