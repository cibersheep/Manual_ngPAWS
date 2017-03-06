### Compatibilidad hacia atrás, o convitiendo de PAWS a ngPAWS

ngPAWS es un fork de Superglus, un clon de PAWS que fue un fork de Paguaglús, un clon puro de PAWS. A través del os años y plataformas  la compatibilidad con el PAWS original no es del 100%. 

Si quieres convetir un juego PAWS a ngPAWS echa un ojo al articulo "[Conversión de PAWS a ngPAWS](Conversión de PAWS a ngPAWS). Probablemente más tarde volverás a este artículo.


### Compatibilidad hacia atrás de los flags del sistema
|PAW FLAG|FUNCION|SOPORTADO\NOTAS|
|------|------|-------|-------|
|0|FLAG_LIGHT|SI||
|1|FLAG_OBJECTS_CARRIED_COUNT|SI||
|2|FLAG_AUTODEC2|SI||
|3|FLAG_AUTODEC3|SI||
|4|FLAG_AUTODEC4|Ver notas|Decrementado cuando no hay luz ni ningún objeto con luz|
|5|FLAG_AUTODEC5|SI||
|6|FLAG_AUTODEC6|SI||
|7|FLAG_AUTODEC7|SI||
|8|FLAG_AUTODEC8|SI||
|9|FLAG_AUTODEC9|SI||
|10|FLAG_AUTODEC10|Ver notas|Decrementado cuando no hay luz ni ningún objeto con luz|
|29|FLAG_PICTURE_SETTINGS|NO||
|30|FLAG_SCORE|SI||
|31|FLAG_TURNS_LOW|SI||
|32|FLAG_TURNS_HIGH|SI||
|33|FLAG_VERB|SI||
|34|FLAG_NOUN1|SI||
|35|FLAG_ADJECT1|SI||
|36|FLAG_ADVERB|SI||
|37|FLAG_MAXOBJECTS_CARRIED|SI||
|38|FLAG_LOCATION|SI||
|39|FLAG_TOPLINE|NO||
|40|FLAG_MODE|NO||
|41|FLAG_PROTECT|NO||
|42|FLAG_PROMPT|NO||
|43|FLAG_PREP|SI||
|44|FLAG_NOUN2|SI||
|45|FLAG_ADJECT2|SI||
|46|FLAG_PRONOUN|SI||
|47|FLAG_PRONOUN_ADJECT|SI||
|48|FLAG_TIMEOUT_LENGTH|SI||
|49|FLAG_TIMEOUT_SETTINGS|Ver notas|Solo soportados bits 0 y 7|
|50|FLAG_DOALL_LOC|SI||
|51|FLAG_REFERRED_OBJECT|SI||
|52|FLAG_MAXWEIGHT_CARRIED|SI||
|53|FLAG_OBJECT_LIST_FORMAT|Ver notas|El bit 7 y 6 funcionan igual, el bit 5 ahora funciona como el 7 pero para  LISTNPC|
|54|FLAG_REFERRED_OBJECT_LOCATION|SI||
|55|FLAG_REFERRED_OBJECT_WEIGHT|SI||
|56|FLAG_REFERRED_OBJECT_LOW_ATTRIBUTES|Ver notas|Contiene los 32 atributos de objeto inferiores en lugar de si el objeto es prenda |
|57|FLAG_REFERRED_OBJECT_HIGH_ATTRIBUTES|See notes|Contiene los 32 atributos de objeto superiores en lugar de si el objeto es contenedor |

|Superglus FLAG|FUNCION|SOPORTADO|NOTAS|
|------|------|-------|-------|
|11|FLAG_ESCAPE|Ver notas|Usado por OBJFOUND y OBJNOTFOUND pero no usado ya por tags de secuencia|
|12|FLAG_PARSER_SETTINGS|SI||


### Compatibilidad de condactos

|Condactos PAW|SOPORTADO|NOTAS|
|-----------|-----------|----------|
|[AT] (AT_ES)|SI||
|[NOTAT] (NOTAT_ES)|SI||
|[ATGT] (ATGT_ES)|SI||
|[ATLT] (ATLT_ES)|SI||
|[PRESENT] (PRESENT_ES)|SI||
|[ABSENT] (ABSENT_ES)|SI||
|[WORN] (WORN_ES)|SI||
|[NOTWORN] (NOTWORN_ES)|SI||
|[CARRIED] (CARRIED_ES)|SI||
|[NOTCARR] (NOTCARR_ES)|SI||
|[CHANCE] (CHANCE_ES)|SI||
|[ZERO] (ZERO_ES)|SI||
|[NOTZERO] (NOTZERO_ES)|SI||
|[EQ] (EQ_ES)|SI||
|[GT] (GT_ES)|SI||
|[LT] (LT_ES)|SI||
|[ADJECT1] (ADJECT1_ES)|SI||
|[ADVERB] (ADVERB_ES)|SI||
|[INVEN] (INVEN_ES)|SI||
|[DESC] (DESC_ES)|SI||
|[QUIT] (QUIT_ES)|SI||
|[END] (END_ES)|SI||
|[DONE] (DONE_ES)|SI||
|[OK] (OK_ES)|SI||
|[ANYKEY] (ANYKEY_ES)|PARCIAL|La implementación en Jacascript es complicada y ahora es un poco precaria. Comprueba cada aparición y si no fucniona bien considera utilizar [BLOCK](BLOCK_ES) o [SOFTBLOCK](SOFTBLOCK_ES)|
|[SAVE] (SAVE_ES)|SI||
|[LOAD] (LOAD_ES)|SI||
|[TURNS] (TURNS_ES)|SI||
|[SCORE] (SCORE_ES)|SI||
|[CLS] (CLS_ES)|SI||
|[DROPALL] (DROPALL_ES)|SI||
|[AUTOG] (AUTOG_ES)|SI||
|[AUTOD] (AUTOD_ES)|SI||
|[AUTOW] (AUTOW_ES)|SI||
|[AUTOR] (AUTOR_ES)|SI||
|[PAUSE] (PAUSE_ES)|Ver notas| Funciona como en PAWS, pero bloquea el juego completamente, por lo que hasta la música de fondo o sonidos se pararán|
|[TIMEOUT] (TIMEOUT_ES)|SI||
|[GOTO] (GOTO_ES)|SI||
|[MESSAGE] (MESSAGE_ES)|SI||
|[REMOVE] (REMOVE_ES)|SI||
|[GET] (GET_ES)|SI||
|[DROP] (DROP_ES)|SI||
|[WEAR] (WEAR_ES)|SI||
|[DESTROY] (DESTROY_ES)|SI||
|[CREATE] (CREATE_ES)|SI||
|[SWAP] (SWAP_ES)|SI||
|[PLACE] (PLACE_ES)|SI||
|[SET] (SET_ES)|SI||
|[CLEAR] (CLEAR_ES)|SI||
|[PLUS] (PLUS_ES)|SI||
|[MINUS] (MINUS_ES)|SI||
|[LET] (LET_ES)|SI||
|[NEWLINE] (NEWLINE_ES)|SI||
|[PRINT] (PRINT_ES)|SI||
|[SYSMESS] (SYSMESS_ES)|SI||
|[ISAT] (ISAT_ES)|SI||
|[COPYOF] (COPYOF_ES)|SI||
|[COPYOO] (COPYOO_ES)|SI||
|[COPYFO] (COPYFO_ES)|SI||
|[COPYFF] (COPYFF_ES)|SI||
|[LISTOBJ] (LISTOBJ_ES)|SI||
|[EXTERN] (EXTERN_ES)|Ver notas|Obviamente no funciona porque llama a código máquina de ZX Specturm El nuevo condacto usa javascript ensu luga y la sintaxis ha cambiado|
|[RAMSAVE] (RAMSAVE_ES)|SI||
|[RAMLOAD] (RAMLOAD_ES)|SI||
|[BEEP] (BEEP_ES)|Ver notas|Ahora reproduce ficheros de sonido y tiene tres parámetros en lugar de dos.|
|[PAPER] (PAPER_ES)|NO|No tiene sentido, para ser aplicado por CSS o tags de secuencia|
|[INK] (INK_ES)|NO|No tiene sentido, para ser aplicado por CSS o tags de secuencia|
|[BORDER] (BORDER_ES)|NO|No tiene sentido, para ser aplicado y creado por CSS o tags de secuencia|
|[PREP] (PREP_ES)|SI||
|[NOUN2] (NOUN2_ES)|SI||
|[ADJECT2] (ADJECT2_ES)|SI||
|[ADD] (ADD_ES)|SI||
|[SUB] (SUB_ES)|SI||
|[PARSE] (PARSE_ES)|SI||
|[LISTAT] (LISTAT_ES)|SI||
|[PROCESS] (PROCESS_ES)|SI||
|[SAME] (SAME_ES)|SI||
|[MES] (MES_ES)|SI||
|[CHARSET] (CHARSET_ES)|NO|Puedes usar CSS para cambiar la fuente|
|[NOTEQ] (NOTEQ_ES)|SI||
|[NOTSAME] (NOTSAME_ES)|SI||
|[MODE] (MODE_ES)|See notes|El flag 40 es modificado Flag 40 pero su uso es ignorado.|
|[LINE] (LINE_ES)|NO|No tiene sentido en HTML|
|[TIME] (TIME_ES)|See notes|Los flags son actualizados, pero solo el primer valor es usado, el otro es ignorado|
|[PICTURE] (PICTURE_ES)|SI||
|[DOALL] (DOALL_ES)|SI||
|[PROMPT] (PROMPT_ES)|Ver notas|Se cambia el Flag 42 pero su valor es ignorado|
|[GRAPHIC] (GRAPHIC_ES)|Ver notas|Solo 0-1, y funciona como una condacto de gráficos on/off. El Flag no se ve afectado|
|[ISNOTAT] (ISNOTAT_ES)|SI||
|[WEIGH] (WEIGH_ES)|SI||
|[PUTIN] (PUTIN_ES)|SI||
|[TAKEOUT] (TAKEOUT_ES)|SI||
|[NEWTEXT] (NEWTEXT_ES)|SI||
|[ABILITY] (ABILITY_ES)|SI||
|[WEIGHT] (WEIGHT_ES)|SI||
|[RANDOM] (RANDOM_ES)|SI||
|[INPUT] (INPUT_ES)|NO|No tiene sentido en HTML|
|[SAVEAT] (SAVEAT_ES)|NO|No tiene sentido en HTML|
|[BACKAT] (BACKAT_ES)|NO|No tiene sentido en HTML|
|[PRINTAT] (PRINTAT_ES)|NO|No tiene sentido en HTML|
|[WHATO] (WHATO_ES)|SI||
|[RESET] (RESET_ES)|NO|Para juegos multiparte, probablemente innecesario actualmente|
|[PUTO] (PUTO_ES)|SI||
|[NOTDONE] (NOTDONE_ES)|SI||
|[AUTOP] (AUTOP_ES)|SI||
|[AUTOT] (AUTOT_ES)|SI||
|[MOVE] (MOVE_ES)|SI||
|[PROTECT] (PROTECT_ES)|NO|No tiene sentido en HTML|


|Condactos de Superglús|ESTADO|NOTAS|
|-----------|-----------|----------|
|[SOUND] (SOUND_ES)|SI||
|[OZERO] (OZERO_ES)|SI||
|[ONOTZERO] (ONOTZERO_ES)|SI||
|[OSET] (OSET_ES)|SI||
|[OCLEAR] (OCLEAR_ES)|SI||
|[ISLIGHT] (ISLIGHT_ES)|SI||
|[ISNOTLIGHT] (ISNOTLIGHT_ES)|SI||
|[DEBUG] (DEBUG_ES)|NO|Ver [Depurando errores con la consola javascript](Depurando errores con la consola javascript)|
|[WRITE] (WRITE_ES)|SI||
|[TRANSCRIPT] (TRANSCRIPT_ES)|SI||
|[VERSION] (VERSION_ES)|SI||
|[WRITE] (WRITE_ES)|SI||
|[WRITELN] (WRITELN_ES)|SI||
|[RESTART] (RESTART_ES)|SI||
|[ATGE] (ATGE_ES)|SI||
|[ATLE] (ATLE_ES)|SI||
|[BCLEAR] (BCLEAR_ES)|SI||
|[BNEG] (BNEG_ES)|SI||
|[BNOTZERO] (BNOTZERO_ES)|SI||
|[BREAK] (BREAK_ES)|SI||
|[BSET] (BSET_ES)|SI||
|[BZERO] (BZERO_ES)|SI||
|[CLEAREXIT] (CLEAREXIT_ES)|SI||
|[DIV] (DIV_ES)|SI||
|[EXITS] (EXITS_ES)|SI||
|[FADEIN] (FADEIN_ES)|SI||
|[GE] (GE_ES)|SI||
|[GETEXIT] (GETEXIT_ES)|SI||
|[HELP] (HELP_ES)|SI||
|[ISMUSIC] (ISMUSIC_ES)|SI||
|[ISNOTMUSIC] (ISNOTMUSIC_ES)|SI||
|[ISNOTSOUND] (ISNOTSOUND_ES)|SI||
|[ISSOUND] (ISSOUND_ES)|SI||
|[LE] (LE_ES)|SI||
|[LOG] (LOG_ES)|SI||
|[MOD] (MOD_ES)|SI||
|[MUL] (MUL_ES)|SI||
|[NPCAT] (NPCAT_ES)|SI||
|[OBJAT] (OBJAT_ES)|SI||
|[OBJFOUND] (OBJFOUND_ES)|SI||
|[OBJNOTFOUND] (OBJNOTFOUND_ES)|SI||
|[ONEG] (ONEG_ES)|SI||
|[PICTUREAT] (PICTUREAT_ES)|SI||
|[RANDOMX] (RANDOMX_ES)|SI||
|[SETEXIT] (SETEXIT_ES)|SI||
|[SETWEIGHT] (SETWEIGHT_ES)|SI||
|[SILENCE] (SILENCE_ES)|SI||
|[TEXTPIC] (TEXTPIC_ES)|SI||
|[VOLUME] (VOLUME_ES)|SI||
|[WHATOX] (WHATOX_ES)|SI||
|[WHATOX2] (WHATOX2_ES)|SI||
|[ZONE] (ZONE_ES)|SI||
|[STRETCH] (STRETCH_ES)|Ver notas|Pendiente|
|[RNDWRITE] (RNDWRITE_ES)|SI||
|[RNDWRITELN] (RNDWRITELN_ES)|SI||
|[WINSPLIT] (WINSPLIT_ES)|NO||
|[GETKEY] (GETKEY_ES)|PARTIAL|La implementación del condacto en javascript es muy difícil y probablemente no funcionará. Comprobar cada caso con detalle|

