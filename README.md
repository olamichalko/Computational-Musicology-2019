## Computational-Musicology-2019

>Tango can be discussed, and we discuss it, but it encloses, as everything that is true, a secret…a French or Spanish composer who threads a tango, discovers, not without surprise, he has threaded something that our ears do not recognize, that our memory does not host, and that our body rejects it could be said that without the sunsets and evenings of Buenos Aires no tango can be made…and that this adventurous species has, however humble, its place on the universe” (Borges in Gomez, 2007/trans. A. Michalko).

Since the 1930s, musicologists and dance specialists have tried to reconstruct and ‘put some systematic order’ into tango origins (Savigliano, 1995). The search for Argentinean tango’s beginnings and authenticity raised many discussions as some historians attribute it to African population connecting it to their rituals and music traditions; others seek its origins in the art of payadores (singers and guitar players from the inside of the country); and some in the arrival of European immigrants at the end of 19th century. The matter of which one of these groups is more entitled to tango will not be discussed here. Instead, I would like to explore and compare the style of two iconic tangueras from 1930s: Ada Falcon and Tita Merello.

### Corpus 
The Corpus consists of tango songs performed by Ada Falcon and Tita Merello. On basis of their dyscographies and recordings, I will search for similarities and differences between those two tangueras. The corpus consists of 600 tracks (300 sung by Ada Falcon and 300 by Tita Merello), which I have chosen randomly from 444 audio tracks of Falcon and 379 audio tracks of Merello. 

falcon <- get_artist_audio_features('ada falcon')
merello <- get_artist_audio_features('tita merello')
ada <- sample_n(falcon,300)
tita <- sample_n(merello,300)

In order to combaine the two samples I had to create a new variable artist_name 

artist_name <-c("AdaFalcon")
ada <- data.frame(artist_name, ada)
artist_name<- c("Tita Merello")
tita <- data.frame(artist_name, tita)

adaytita <-rbind("ada","tita")

### Preliminary analysis 

#The comparison of modes shows that Tita Merello sings predominantly in the Major mode (37 out of 50 songs), whereas Ada Falcon is more equilibrated.


![modetitayada](modetitayada.png)

#Furthermore, I looked at the keys used by both ladies and it results that Tita Merello sings predominantly in A#, B and G, whereas Ada Falcon in A, A# and C. Interesting is the fact that Tita Morello did not sing even one song in key C (on basis of this sample). 

![keytitayada](keytitayada.png)

#By comparing means of danceability, speechiness, tempo, valence and energy we can conclude that there exist significant differences between Falcon and Merello on features such as valence (M = 0.55 vs 0.69, respectively, p-value of a two-sided t-test=9.84e-07), tempo (M= 100.20 vs 123.29, p-value of a two-sided t-test=6.23e-06 ) , energy (M= 0.23 vs 0.35, p-value of a two-sided t-test=4.30e-09), speechiness (M= 0.24 vs 0.14, p-value of a two-sided t-test=8.66e-05) but not on danceability(M= 0.63 vs 0.64, p-value of a two-sided t-test = 0.60). In general, except the speechiness, all features of Tita Morello give higher values than the ones of Ada Falcon. 

t.test(ada$valence,tita$valence)
t.test(ada$tempo,tita$tempo)
t.test(ada$energy,tita$energy)
t.test(ada$danceability,tita$danceability)
t.test(ada$speechiness,tita$speechiness)


#For both artists the standard deviation of tempo is large: Ada sd=25.62 and Tita sd= 22.54. It may be due to the significant variability of tempi across the songs, for instance, the min and max tempo of Ada Falcon's songs is 55.10 and 149.30 respectively. For Tita is min tempo 82.69 and max tempo 179.60. In general the distributions of individual audio features of Merello and Falcon are not normally distributed.    



“If one wants eternal tango, one has to admit changing tango, because the substance of tango does not reside in the 2 for 4 nor in four for eight, but in change. And the constant change demands/requires constant searching, the constant experimentation.
Si se quiere un tango eterno hay que admitir un tango cambiante, porque la sustancia del tango no reside en los dos por cuatro y ni en el cuatro por ocho, sino en el cambio. Y el cambio permanente exige la permanente búsqueda, la experimentación permanente (Gobello,1980).

References: 
Gobello, J. (1980). Crónica general del tango (No. 78 (091)). Fraterna.
Gomez, A. (2009). Ultimo patio. Turmalina.
