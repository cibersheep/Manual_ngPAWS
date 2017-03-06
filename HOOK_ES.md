**HOOK "string"**

Llama al hook de código con el sring como parámetro. 

Se trata de una poderosa acción que se apoya en librerías externas. Un autor  de ngPAWS rara vez lo usará, aunque pueden encontrarse en [[la base de datos de inicio|la base de datos de inicio]].

El autor de la librería puede modificar la variable done_flag para determinar si tras llamar al hook el proceso llamante debe finalizar o no. Es algo que se puede hacer directamente (done_flag=true) o llamando a ACCdone().

Ver también:

[[Hooks|Hooks_ES]]