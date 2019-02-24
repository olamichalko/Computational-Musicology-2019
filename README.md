---
title: "Secrets of tango"
data: cantro
output: 
  flexdashboard::flex_dashboard:
    orientation: rows
    vertical_layout: fill
    theme: journal
---

```{r setup, include=FALSE}
library(flexdashboard)
library(tidyverse)
library(spotifyr)
library(plotly)
library(ggplot2)
py<- plotly(username = "aleksandram", key= "••••••••••")
```


```{r global, include=FALSE}
data(cantro)
```

Gotán
===============================================================================================================
Introduction {data-width=350}
-----------------------------------------------------------------------

### **Borges on Tango**

"Tango can be discussed, and we discuss it, but it encloses, as everything that is true, a secret…a French or Spanish composer who threads a tango, discovers, not without surprise, he has threaded something that our ears do not recognize, that our memory does not host, and that our body rejects it could be said that without the sunsets and evenings of Buenos Aires no tango can be made…and that this adventurous species has, however humble, its place on the universe” (Borges in Gomez, 2007/trans. A. Michalko).

Origins of Tango {data-width=450}
-----------------------------------------------------------------------

###**Origins of Tango**

Since the 1930s, musicologists and dance specialists have tried to reconstruct and ‘put some systematic order’ into tango origins (Savigliano, 1995). The search for Argentinean tango’s beginnings and authenticity raised many discussions as some historians attribute it to African population connecting it to their rituals and music traditions; others seek its origins in the art of payadores (singers and guitar players from the inside of the country); and some in the arrival of European immigrants at the end of 19th century. The matter of which one of these groups is more entitled to tango will not be discussed here. Instead, I would like to explore and compare the style of two iconic tango orchestras: Orquesta de Francisco Canaro and Orquesta de Anibal Troilo. The orchestra of Canaro was active mostly between 1920-1940s and orchestra of Troilo after 1940s. One remarkable differance is that Canaro performed mostly with female singers whereas Troilo with male tangueros. I will analyze their dyscographies in order to find some other differances and similarities between them. Perhaps, this analyisis will reveal some secrets of tango. 

Corpus {data-width=200}
-----------------------------------------------------------------------

### **Corpus**

The Corpus consists of tango songs performed by Ada Falcon and Tita Merello. On basis of their dyscographies and recordings, I will search for similarities and differences between those two tango orchestras. The corpus consists of 608 tracks (304 performed by Orquesta de Canaro and 304 by de Orquesta de Troilo). 

First Steps
==============================================================================================================
### **Being in Tango mode**

The analysis of the songs' modes does not show any significant differances.The Orquesta de Canaro has slightly more songs in major mode than the Orquesta de Troilo and the Orquesta de Troilo has slightly more songs in minor mode than the Orquesta de Canaro.



### **The right key**

The comparison of key modes shows that Canaro's tracks are predominantly in D major,A major, C# major and G major, E major, whereas Troilo's tracks are in F major, G major, C major, D major, f minor and d minor. 

### **Tango all around**

In general, the data of audio features of tango songs does not have a normal distribution. 

Further Analysis
==============================================================================================

###**Tango means...

By comparing means of danceability, tempo, valence and energy we can see some differances, however, how significant they are, still needs to be determined. The mean (M) and  standard deviation (sd) of danceability feature for Canaro are 0.66 and 0.12 respectively. For Troilo M = 50 and sd = 0.10. The valence for Canaro: M = 0.71, sd = 0.14 and for Troilo: M= 0.59 and sd = 0.16. The energy for Canaro: M = 0.27, sd = 0.09 and for Troilo: M= 0.31, sd = 0.11. In general the means of Canaro's audio features are higher than the ones of Troilo with exception of energy feature.  

```{r, fig.width=2, fig.height=2}
plot2<- ggplot(cantro,aes(x=orquesta, y= danceability, color = orquesta))+
   geom_boxplot()+
   theme(panel.background = element_rect(fill = "white"))+
   theme(panel.grid.major = element_line(colour = "grey"))+
   theme(legend.position = "none")
ggplotly(plot2)
```
```{r, fig.width=2, fig.height=2}
plot3<- ggplot(cantro,aes(x=orquesta, y= energy, color = orquesta))+
   geom_boxplot()+
   theme(panel.background = element_rect(fill = "white"))+
   theme(panel.grid.major = element_line(colour = "grey"))+
   theme(legend.position = "none")
ggplotly(plot3)
```



###**Tango Pace***

```{r, fig.width=2, fig.height=2}
plot1<- ggplot(cantro,aes(x=orquesta, y= tempo, color = orquesta))+
   geom_boxplot()+
   theme(panel.background = element_rect(fill = "white"))+
   theme(panel.grid.major = element_line(colour = "grey"))+
   theme(legend.position = "none")
ggplotly(plot1)
```

***

For both orchestras the mean of tempo is around 120: Orquesta de Canaro M = 121, sd=17.3 and Orquesta de Troilo M = 117, sd 17.1.54 and Tita sd= 24.21. Due to the significant variability of tempi across the songs the differance between the min en max values is rather large. For instance, the min and max tempo of Orquesta de Canaro is 57.56 and 193.74 respectively. For Orquesta de Troillo the min tempo is 57.24 and max tempo 186.18. Indeed, the diversity and changeability of tempi in tango is one of its fundamentals. Also, because of tango's mutable and mercurial character, non-normal distribution in all audio features is observed. Due to these observations I will not consider extreme values of data set as outliers.

###**Next steps**


In the further analysis I would like to combine various variables and examine their interdependency and perhaps find some tendencies and patterns. 

"If one wants eternal tango, one has to admit changing tango, because the substance of tango does not reside in the 2 for 4 nor in four for eight, but in change. And the constant change demands/requires constant searching, the constant experimentation" (Gobello,1980/Trans. A. Michalko).

References: 
Gobello, J. (1980). *Crónica general del tango* (No. 78 (091)). Fraterna.
Gomez, A. (2009). *Ultimo patio*. Turmalina.
Savigliano, M. (1995). *Tango and the political economy of passion.* Westview Press.


Tango Night Fever 
======================================================================================================
###**Milonga**

The tango songs recorded by Orquesta de Canaro and Orquesta de Troilo are made for dancing tango. The tango dancers are perfectly able to dance along with the music and no editing of audio is needed in order to make those audio tracks suitable for milongas. However, having in mind a non-normal distribution of variables across all data (preliminary analysis), I want to have a closer look at the relations between danceability and energy, danceability and valence and danceability and tempo. 

###**Mezclando**

First, I will look at the relation between danceability and energy. I grouped the observations by the name of the orchestra. 

```{r, fig.width=2, fig.height=2}
plot4<- ggplot(cantro, aes(x= energy, y = danceability, group = orquesta))+
  geom_jitter(aes(color=mode, shape = orquesta), alpha = 0.6)+
  geom_smooth(aes(color=orquesta), se = FALSE)+
  theme(panel.background = element_rect(fill = "white"))+
  theme(panel.grid.major = element_line(colour = "grey"))+
  theme(legend.title = element_blank())
ggplotly(plot4)
```

***

In both cases the danceability decreases when energy increases.


The next figure shows the relation between danceability and valence. Again there is no significant differance between interdependency of two features among Orquesta de Canaro and Orquesta de Troilo: in both cases the danceability gradually increases with the increase of the valence.

```{r, fig.width=2, fig.height=2}
plot5<- ggplot(cantro, aes(x= valence, y = danceability, group = orquesta))+
  geom_jitter(aes(color=mode, shape = orquesta), alpha = 0.6)+
  geom_smooth(aes(color=orquesta), se = FALSE)+
  theme(panel.background = element_rect(fill = "white"))+
  theme(panel.grid.major = element_line(colour = "grey"))+
  theme(legend.title = element_blank())
ggplotly(plot5)
```



The last figure shows the relationship between danceability and tempo. The scatterplot confirms the findings of preliminary analysis: the perfect tempo to dance tango seems to be ca 120.         

```{r, fig.width=2, fig.height=2}
plot6<- ggplot(cantro, aes(x= tempo, y = danceability, group = orquesta))+
  geom_jitter(aes(color=mode, shape = orquesta), alpha = 0.6)+
  theme(panel.background = element_rect(fill = "white"))+
  theme(panel.grid.major = element_line(colour = "grey"))+
  theme(legend.title = element_blank())
ggplotly(plot6)
```

The comparison of interdependencies among various aduio features did not demonstrate that the recordings of two orchestras would follow individual/peculiar patterns. On contrary, in those three scatterplots, the orchestras seem to follow similar patterns. Perhaps, more detailed analysis of particular songs will reveal more differances between those tango orchestras. For instance, analysis of the same tango song.

Time Wrapping
==============================================================================================

```{r echo = FALSE}
library(tidyverse)
library(spotifyr)
source(Sys.setenv(SPOTIFY_CLIENT_ID = '1d4971665401496da57cca2a4016e328'),
Sys.setenv(SPOTIFY_CLIENT_SECRET = '63fa15e1b5cc4e0ab91504cd3d593946'))
```
###Frame1
```{r}
troilocumparsita <- 
    get_tidy_audio_analysis('1JBKRHTmrRzUZkSGqAhbyT') %>% 
    select(segments) %>% unnest(segments) %>% 
    select(start, duration, pitches)
canarocumparsita <- 
    get_tidy_audio_analysis('4IvBCYb0koQVUFr42fUUUy') %>% 
    select(segments) %>% unnest(segments) %>% 
    select(start, duration, pitches)
```    

```{r}
compmus_long_distance(
    troilocumparsita %>% mutate(pitches = map(pitches, compmus_normalise, 'chebyshev')),
    canarocummparsita %>% mutate(pitches = map(pitches, compmus_normalise, 'chebyshev')),
    feature = pitches,
    method = 'euclidean') %>% 
    ggplot(
        aes(
            x = xstart + xduration / 2, 
            width = xduration,
            y = ystart + yduration / 2,
            height = yduration,
            fill = d)) + 
    geom_tile() +
    scale_fill_continuous(type = 'viridis', guide = "none") +
    labs(x = 'La cumparsita troilo', y = 'La cumparsita canaro') +
    theme_minimal()
```
###Frame2
```{r}
troiloyira <- 
    get_tidy_audio_analysis('4HpKs8OMi5EdtoUKStZUgn') %>% 
    select(segments) %>% unnest(segments) %>% 
    select(start, duration, pitches)
canaroyira <- 
    get_tidy_audio_analysis('5ljfT068prmeEkF0N1Bgc6') %>% 
    select(segments) %>% unnest(segments) %>% 
    select(start, duration, pitches)
```    

```{r}
compmus_long_distance(
    troiloyira %>% mutate(pitches = map(pitches, compmus_normalise, 'chebyshev')),
    canaroyira %>% mutate(pitches = map(pitches, compmus_normalise, 'chebyshev')),
    feature = pitches,
    method = 'euclidean') %>% 
    ggplot(
        aes(
            x = xstart + xduration / 2, 
            width = xduration,
            y = ystart + yduration / 2,
            height = yduration,
            fill = d)) + 
    geom_tile() +
    scale_fill_continuous(type = 'viridis', guide = "none") +
    labs(x = 'Yira Canaro', y = 'YIra Troilo') +
    theme_minimal()
```