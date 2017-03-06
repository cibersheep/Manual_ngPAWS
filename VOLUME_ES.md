VOLUME canal valor

Especifica el volumen para el sonido sonando en el canal "canal". Para dar el valor máximo de volumen el valor ha de ser 65535, para silenciarlo en valor ha de ser 0. Cualquier valor intermedio dara un volumen entre el silencio y el máximo (por ejemplo 37868 es un 50% del volumen máximo).

* Notese que el volumen solo afectará si hay un sonido en ese canal.

* También ten en cuenta que aunque el volumen se ponga a 0, eso no significa que no siga siendo reproducido en silencio, por lo que ISMUSIC o ISSOUND se cumplirán en ese canal.

