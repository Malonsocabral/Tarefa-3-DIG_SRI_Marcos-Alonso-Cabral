# Tarefa-3-DIG_SRI_Marcos-Alonso-Cabral
## 1.Realiza unha consulta "dig danielcastelao.org" e identifica cada parte da resposta (IN, CNAME, A, QUERY SECTION, ANSWER SECTION, AUTHORITY SECTION, etc)
>[!NOTE]
>Para ver a tarefa dun modo mais visual con todos os seguintes pasos con fotos, deixo a continuacion un link a google docs.[LINK_DOCUMENTO](https://docs.google.com/document/d/12FToQXLYr0cREJN4_N-fhwKtCSm_ihytPgrDggFdjEE/edit)

A consulta **"dig danielcastelao.org"** devolve as seguintes seccións:

### 1. QUERY SECTION (Sección de consulta)
Mostra a consulta realizada.

- **danielcastelao.org**: dominio consultado.
- **IN**: clase de protocolo (Internet).
- **A**: tipo de rexistro solicitado (rexistro A, que devolve unha IP).

### 2. ANSWER SECTION (Sección de respostas)
Devolve os rexistros DNS solicitados.

- **danielcastelao.org**: dominio consultado.
- **3600**: TTL (tempo que a resposta pode gardarse en caché).
- **IN**: clase do protocolo.
- **A**: tipo de rexistro (rexistro A).
- **185.68.109.101**: dirección IP asociada ao dominio.

### 3. AUTHORITY SECTION (Sección de autoridade)
Lista os servidores DNS autoritativos.

- **NS**: rexistro que indica os servidores de nomes autoritativos.

### 4. ADDITIONAL SECTION (Sección adicional)
Mostra información adicional, como as IPs dos servidores autoritativos.


### 5. HEADER SECTION (Cabeceira)
Información xeral sobre a consulta e a resposta.

- **status: NOERROR**: indica que a consulta foi exitosa.

### 6. CNAME (Canonical Name)
Rexistro que indica que un dominio é un alias doutro.
































## 2.Realiza consutas dos seguintes nomes e identifica as diferencias: moodle.danielcastelao.org, www.danielcastelao.org  
Como podemos ver en el documento de goolge las principales diferencias es que la de www.danielcastelao.org tiene la QUESTION SECTION Y ANSWER QUIESTION mientras que la de moodle.danielcastelao.org tiene QUESTION SECTION Y AUTHORITY SECTION SECTION.
Ademas como podemos observar a paxina de moodle é un subdominio da de danielcastelao. Sin embargo acontinuacion voy a explicar de maneira mais especifica o que ocorre tras poñer os comandos `dig www.danielcastelao.org` e `dig moodle.danielcastelao.org`

A continuación realízanse consultas para **moodle.danielcastelao.org** e **www.danielcastelao.org**, identificando as diferencias entre ambos.

### 1. Consulta para **moodle.danielcastelao.org**

- **moodle.danielcastelao.org**: subdominio consultado.
- **3600**: TTL.
- **A**: tipo de rexistro, que resolve a unha dirección IP.
- **185.68.109.102**: IP asociada a este subdominio.

### 2. Consulta para **www.danielcastelao.org**
- **www.danielcastelao.org**: subdominio consultado.
- **CNAME**: este rexistro indica que é un alias de **danielcastelao.org**.
- **danielcastelao.org**: dominio ao que apunta o alias.
- **185.68.109.101**: IP asociada ao dominio principal.

### Diferencias
1. **moodle.danielcastelao.org** resolve directamente a unha dirección IP (**rexistro A**).
2. **www.danielcastelao.org** é un alias (**rexistro CNAME**) que apunta a **danielcastelao.org**, e logo este resolve á IP 185.68.109.101.




## 3.Averigua o nome e IP dos servidores de DNS autoritativos de www.danielcastelao.org, por qué soen ser 2 servidores autoritativos?


### Nome e IP dos servidores DNS autoritativos de **www.danielcastelao.org**
Na consulta DNS co comando `dig ns www.danielcastelao.org` para **www.danielcastelao.org**, os servidores DNS autoritativos pódense atopar na **AUTHORITY SECTION**. Os servidores identificados poden ser:

**ns1.hover.com** e **dnsmaster.hover.com**

>[!NOTE]
>Cabe destacar que isto pode verse de manera visual no documento de google do comenzo.




## 4.Realiza as consultas de nomes inversas: 130.206.164.68 e de outras dúas IPs que se che ocorran.

Para realizar a inversa de esta ip debemos utilizar o comando `dig -x 130.206.164.68` xa que co parametro -x facemos a inversa.

Logo podemos ver  os outras dous ips al azar que elexin. A primeira é 130.206.164.69 e a segunda 130.206.164.70. En ambos volvin a utilizar o comando `dig -x <ip>`

>[!NOTE]
>Cabe destacar que isto pode verse de manera visual no documento de google do comenzo.





## 5.A qué servidor DNS estás consultando? Cómo o podes cambiar sen tocar os ficheiros de configuración do sistema?
Para saber este servidor DNS fai falta poñer o comando `cat /etc/resolv.conf`.Por defecto este archivo ten configurado os servidores DNS que se usan para que o propio comando **dig** resolva os nomes de dominios.  
Para lograr cambiar esto, soamente debemos usar o comando `dig @8.8.8.8 www.danielcastelao.org` para asi buscar dende o 8.8.8.8 (indicado mediante o *@*) que basicamente é google.








## 6.Obtén o rexistro SOA (Start of Authority) do dominio  moodle.danielcastelao.org preguntándolle ó servidor DNS de google e logo preoguntándollo directamente ó servidor primario do dominio danielcastelao.org. 

Neste exercicio utilizaremos o comando `dig @8.8.8.8 SOA moodle.danielcastelao.org` e segun o explicado anteriormente, podemos saber que se busca directamente dende o DNS de google polo *@* ao comenzo do comando.  

E basicamente a resposta que nos aparece na parte da autoridade é a seguinte : danielcastelao.org. 300 IN SOA ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300  

>[!NOTE]
>Cabe destacar que isto pode verse de manera visual no documento de google do comenzo.

Logo, procedemos a preguntarlle ao servidor primario utilizando o comando `dig @ns1.hover.com. SOA moodle.danielcastelao.org`.  
Unha vez feita a consulta o que nos devolve na authority section do dominio principal do danielcastelao.org é o seguinte : danielcastelao.org. 300 IN SOA ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300

>[!NOTE]
>Isto podese ver de manera visual no documento de google do comenzo.

## 7.Consulta a IP de www.elpais.com. Cánto tempo queda almaceado o rexistro de recurso no DNS local?, se preguntas ó DNS local por este recurso, qué observas no TTL do rexistro?

Para consultar a ip de *elpais* debemos facer o seu correspondiente comando dig, que neste caso quedaria tal que asi : `dig www.elpais.com`  
Logo podemos observar que na answer section o servidor nos devuelve o seguinte :    
www.elpais.com.		297	IN	CNAME	prisa-us-eu.map.fastly.net.
prisa-us-eu.map.fastly.net. 60	IN	A	199.232.194.133
prisa-us-eu.map.fastly.net. 60	IN	A	199.232.198.133
É como podemos observar o TTL é de 297

    
## 8.Busca o TTL de distintos nomes de dominio de servicios que escollas, a qué se poden deber as diferencias?

Para comenzar elexin os nomes de dominio de google.com, tesla.com e agar.io  
Os comandos foron os seguintes : `dig www.google.com`, `dig www.tesla.com` e `www.agar.io`.  

>[!NOTE]
>Isto podese ver de manera visual no documento de google do comenzo.

   
Podemos observar que o TTL de google non aparece posiblemente porque o dominio de google sera para sempre. 
Logo, no caso de tesla podemos ver que o TTL é de **21436** , o cal nos da a enterner que tamen é moi alto xa que no se esperan cambios nesta paxina.
E por ultimo no caso de agar.io podemos ver que o TTL é de **300** xa que pode ser mais probable que esta paxina sufra cambios en comparacion coa de tesla e google



## 9.Determina o TTL máximo (original) dun nome de dominio.
    
No caso de tesla.com, tras moita invertigacion, pode dicir que a paxina de tesla no ten un TTL maximo como tal sinon que segue o standar (3600) aunque se facemos o comando dig neste momento (`dig www.tesla.com`) aparecenos como TTL de **21436**

## 10.Averigua cántas máquinas con distintas IPs están detrás do dominio web www.google.es, sempre son as mesmas e na mesma orde? por qué?

Para averiguar cantas maquinas estan detras de este dominio debemos facer o comando `dig www.google.es` para asi comprobar que so aparece unha maquina no momento que realicei esta peticion.  
>[!NOTE]
>Isto podese ver de manera visual no documento de google do comenzo.
E para responder as preguntas, si, si son sempre has mismas maquinas polo menos nas consultas que eu fixen ao servidor, e supoño que sera porque é una empresa estable que sabe que ese servicio vai funcionarlle.

## 11.Pregunta o mesmo a un server raiz (J.ROOTSERVERS.NET por exemplo) e comproba na resposta se o server acepta o modo recursivo

Neste caso a facer o comando dig a propia raiz debemos poñer o seguinte `dig A J.ROOTSERVERS.net`
Logo podemos ver que na parte da resposta (answer section) pon duas ips : J.ROOTSERVERS.net.	3600	IN	A	15.197.204.56
J.ROOTSERVERS.net.	3600	IN	A	3.33.243.145  


  
## 12.Se queremos ver tóda-las queries que fai o servidor de DNS, qué opción temos que usar? averigua a IP de www.timesonline.co.uk, especifica os pasos dados

## 13.Usando a información dispoñible a traveso do DNS especifica a máquina (nome e IP) ou máquinas que actúan como servers de correo do dominio danielcastelao.org

## 14.Podes obter os rexistros AAAA de www.facebook.com? a qué corresponden?

Entrega as respostas nun arquivo .md gardado nun repositorio git

