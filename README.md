# Mapas interativos com python

Este repositório contém um projeto desenvolvido utilizando python.

### Pré-requisitos

Antes de começar, verifique se você possui a seguinte ferramentas instaladas em sua máquina:

- folium


### Passo 1: instalar a biblioteca  

Caso não tenha a biblioteca instalada em seu ambiente. utilize o comando abaixo para instalar a mesma.  

```python

!pip install folium

```

Espere completar a instalação e só curtir. 

---

Depois de carregar o Folium podemos executar ele diretamente e plotar um mapa sem muita "frescura", 

```python
# Para executar o folium é necessário apenas executar o Map()
folium.Map()

```

agora para melhor visualização e colocar pontos específicos utilizamos o location,

```python

# Para ficar mais interessante e melhor vamos adicionar coordenadas centrais.
lat,lon= -30.0158,-51.1348
mapa = folium.Map(location=(lat,lon))
mapa

```


No exemplo acima colocamos as coordenadas do município de Porto Alegre no Rio Grande do Sul. 

Podemos colocar um zoom no mapa, para visualizar exatamente a área desejada. 

```python

# Podemos iniciar com um Zoom, para melhor observação ou detalhamento da área desejada.
mapa = folium.Map(
    location=(lat,lon),
    zoom_start= 11
                    )
mapa

```

Pode também adicionar um zoom final, que limita até onde o seu zoom na imagem pode ir, útil para quando quer limitar o que o usuário pode ver no mapa. 


```python

# podemos adicionar um zoom final, estabelecendo um limite de zoom para o nosso mapa 
mapa = folium.Map(
    location=(lat,lon),
    zoom_start= 11,
    max_zoom= 15
                    )
mapa

```

assim como pode realizar o procedimento inverso, definir o zoom minímo possível pelo usuário usando a função min_zoom.

Podemos estilizar o mapa mudando o tema. 
Como por exemplo definir o mapa com tons de cinzas ou black. 


```python

# mapa todo preto e cinza. 
mapa = folium.Map(
    location=(lat,lon),
    tiles = 'CartoDB dark_matter',
                    )
mapa

```
Ou cinza .

```python

# mapa em escalas de cinza. 
mapa = folium.Map(
    location=(lat,lon),
    tiles = 'CartoDB positron',
                    )
mapa

```

Podemos adicionar marcadores de localização,de pontos turisticos, residencias etc ..



```python

# Podemos adicionar marcadores no nosso mapa

folium.Marker(
    location = [-29.9739, -51.1949],
    popup = 'Arena do Grêmio',
    icon = folium.Icon(color = 'blue', prefix= "glyphicon", icon= 'spinner')
).add_to(mapa)
mapa
```


Nesse marcamos a posição da arena do Grêmio no mapa

Também é possível adicionar um conjunto de marcadores, criando uma lista e utilizando um laço de repetição for, igual ao exemplo abaixo.


```python

# PODEMOS ADICIONAR LISTAS DE PONTOS .  Mas, para isso é necessário um laço de repetição 
nomes  = [ 'Morro Santana',  'Parque Natural Municipal Saint-Hilaire', 'UFRGS Campus Centro',
	'Aeroporto', 'Rodoviária', 'Parque Germânia' , 'Porto Alegre Country club', 
	'Parque Farroupilha', 'Cidade Baixa', 'Centro Histórico', 'Parque da Redenção', ' Orla do Guaíba', 'Sport Club Internacional', 'Arena do Grêmio '
	]

loc =[ 
	[-30.0534, -51.1259],
	[-30.1030, -51.0955],
	[-30.0332, -51.2204],
	[-29.9933, -51.1724],
	[-30.0228, -51.2196],
	[-30.0254, -51.1578],
	[-30.0244, -51.1677],
	[-30.0367, -51.2153],
	[-30.0405, -51.2225],
	[-30.0326, -51.2312],
	[-30.0359, -51.2118],
	[-30.0544, -51.2331],
	[-30.0656, -51.2360],
	[-29.9739, -51.1949]
	]

for i in range(len(loc)):
    folium.Marker(
    location =  loc[i],
    popup = nomes[i],
    icon = folium.Icon(color = 'blue', prefix= 'glyphicon glyphicon-camera ', icon= 'spinner', icon_color= ' white')
).add_to(mapa)
mapa


```

A titulo de informação, podemos adicionar circulos ao redor de determinados pontos, Como no exemplo abaixo 


```python

# Podemos criar circulos ao redor de pontos. 
folium.CircleMarker(
    location = [-29.9739, -51.1949], # ARENA DO GREMIO COORDENADAS.
    radius= 15, # raio do circulo 
    color = 'blue', # cor do entorno do circulo criado
    fill = True, # declarar se quer que preencha a celula ou não
    fill_color = "yellow" # cor de preenchimento do circulo criado
).add_to(mapa)
mapa

```

e por fim podemos salvar o mapa caso desejado. 

```python


mapa.save("Pontos_turisticos_PoA.html")

```

## Considerações finais

Com o Folium, é possível criar mapas profissionais com poucos comandos. Ele é ideal para quem trabalha com dados espaciais e deseja compartilhar informações de forma visual e interativa. Combinado com dados geográficos reais e boas práticas de visualização, você pode levar seus projetos a outro nível.


