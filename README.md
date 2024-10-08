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
Na consulta DNS co comando `dig www.danielcastelao.org` para **www.danielcastelao.org**, os servidores DNS autoritativos pódense atopar na **AUTHORITY SECTION**. Os servidores identificados poden ser:

**ns1.hover.com** e **dnsmaster.hover.com**

>[!NOTE]
>Cabe destacar que esto puede verse de manera visual en el documento de google del comienzo.




## 4.Realiza as consultas de nomes inversas: 130.206.164.68 e de outras dúas IPs que se che ocorran.

Para realizar a inversa de esta ip debemos utilizar o comando `dig -x 130.206.164.68` xa que co parametro -x facemos a inversa.

Logo podemos ver  os outras dous ips al azar que elexin. A primeira é 130.206.164.69 e a segunda 130.206.164.68. En ambos volvin a utilizar o comando `dig -x <ip>`

>[!NOTE]
>Cabe destacar que esto puede verse de manera visual en el documento de google del comienzo.





## 5.A qué servidor DNS estás consultando? Cómo o podes cambiar sen tocar os ficheiros de configuración do sistema?
Para saber este servidor DNS fai falta poñer o comando `cat /etc/resolv.conf`







## 6.Obtén o rexistro SOA (Start of Authority) do dominio  moodle.danielcastelao.org preguntándolle ó servidor DNS de google e logo preoguntándollo directamente ó servidor primario do dominio danielcastelao.org. 

## 7.Consulta a IP de www.elpais.com. Cánto tempo queda almaceado o rexistro de recurso no DNS local?, se preguntas ó DNS local por este recurso, qué observas no TTL do rexistro?
    
## 8.Busca o TTL de distintos nomes de dominio de servicios que escollas, a qué se poden deber as diferencias?

## 9.Determina o TTL máximo (original) dun nome de dominio.
    
## 10.Averigua cántas máquinas con distintas IPs están detrás do dominio web www.google.es, sempre son as mesmas e na mesma orde? por qué?

## 11.Pregunta o mesmo a un server raiz (J.ROOTSERVERS.NET por exemplo) e comproba na resposta se o server acepta o modo recursivo
    
## 12.Se queremos ver tóda-las queries que fai o servidor de DNS, qué opción temos que usar? averigua a IP de www.timesonline.co.uk, especifica os pasos dados

## 13.Usando a información dispoñible a traveso do DNS especifica a máquina (nome e IP) ou máquinas que actúan como servers de correo do dominio danielcastelao.org

## 14.Podes obter os rexistros AAAA de www.facebook.com? a qué corresponden?

Entrega as respostas nun arquivo .md gardado nun repositorio git

