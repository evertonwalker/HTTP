# Curso sobre o que é HTTP

HTTP ( Hypertext Transfer Protocol ) é um protocolo que define as regras de comunicação entre cliente e servidor na internet, fazendo uma analogia pra o nosso mundo, enquanto duas pessoas
conversam elas precisam estabelecer uma comunicação de forma que uma entenda a outra, no mundo da internet, isso não é diferente, então assim como pra duas pessoas conversarem precisa de um
idioma comum, na internet precisa de um protocolo que as duas partes entedam.

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/http-cliente-servidor-protocolo.png)

Pontos interresantes sobre HTTP:

- Na internet sempre tem um cliente e um servidor
- Entre o cliente e o servidor precisam haver regras de comunicação
- As regras são definidas dentro de um protocolo
- HTTP é o protocolo mais importante na internet
- Todos os dados enviados entre cliente e servidor são transmitidos em texto puro, inclusive dados sensíveis, como login e senha ( Bastante perigoso ) !

# HTTPS 

Sabendo que com o mundo tem vários meios até seu dado chegar ao servidor e voltar como, wifi, servidores de redirecionamento e etc, os desenvolvedores não poderiam
deixar esses dados sendo trafegados de maneira aberta, seria muito perigoso, principalmente se fosse por exemplo dados bancários?

Então surgiu o HTTPS, que basicamente é o HTTP comum, porém com uma camada adicional de segurança/criptografia que antes era SSL, mas posteriormente passou a ser também TLS.
É muito comum que estas duas siglas sejam encontradas juntas como SSL/TLS por se tratarem da mesma questão de segurança. Sendo assim, temos dois termos:

SSL/TLS: Secure Sockets Layer / Transport Layer Security

Essa troca de informação funciona através de chaves públicas e privadas, que ficam entre o navegador e o servidor, de forma que só um consiga descriptografar o dado do outro lado, isso
acontece através do <b>Certificado digital </b> e para que ele serve? Um certificado digital prova uma identidade para um site, onde temos informações sobre o seu domínio e a data de expiração 
desse certificado Além disso, o certificado ainda guarda a chave pública que é utilizada para criptografar (cifrar) os dados que são trafegados entre cliente e servidor.

Esses <b> Certificados digitais </b> só podem ser obtidos através de uma autoridade certificadora, para poder comprovar que podemos confiar naquele certificado (identidade).


<h2>Tipos de criptografia </h2>

# Criptografia assimétrica

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/cripto-assimetrica.png)

Existem a chave pública e uma chave privada. As chaves estão ligadas matematicamente, o que foi cifrado pela chave pública só pode ser decifrado pela chave privada. Isso garante que os dados cifrados pelo navegador (chave pública) só podem ser lidos pelo servidor (chave privada). Como temos duas chaves diferentes envolvidas, esse método de criptografia é chamado de criptografia assimétrica. No entanto, a criptografia assimétrica tem um problema, ela é lenta.

# Criptografia simétrica

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/cripto-simetrica.png)

Ela usa a mesma chave para cifrar e decifrar os dados, como na vida real, onde usamos a mesma chave para abrir e fechar a porta. A criptografia simétrica é muito mais rápida, mas infelizmente não tão segura. Como existe apenas uma chave, ela ficará espalhada pelos clientes (navegadores) e qualquer um, que tem a posse dessa chave, pode decifrar a comunicação.

<b> Ponto mais interessante sobre isso é </b> que o HTTPS usa ambos os métodos de criptografia, assimétrica e simétrica. Como assim? Muita calma, tudo o que aprendemos é verdade! Só faltou o grande final :)

No certificado, vem a chave pública para o cliente utilizar, certo? E o servidor continua na posse da chave privada, ok? Isso é seguro, mas lento e por isso o cliente gera uma chave simétrica ao vivo. Uma chave só para ele e o servidor com o qual está se comunicando naquele momento! Essa chave exclusiva (e simétrica) é então enviada para o servidor utilizando a criptografia assimétrica (chave privada e pública) e então é utilizada para o restante da comunicação.

Então, HTTPS começa com criptografia assimétrica para depois mudar para criptografia simétrica. Essa chave simétrica será gerada no início da comunicação e será reaproveitada nas requisições seguintes. Bem-vindo ao mundo fantástico do HTTPS.

# Endereços

Os endereços podem ser dividos em categorias de assuntos que envolvem <b>domínio, subdomínio, ips e DNS </b>, basicamente são informações que precisamos saber para acessar um determinado site em um
servidor, vamos entender como funciona: 

O domínio é a principal url do site por exemplo: www.alura.com.br, a abreviação www siginfica <b> world wide web</b> a maioria dos sites hoje em dia não utiliza isso é algo legado.
Se você analizar o domínio da direita pra esquerda vai ver que o <b>br</b> está no Top domain level, e o -> <b>com e alura</b> são subdomínios desse domínio principal

Existem outros tipos de subdomínios como o do google que usam para o gmail e o drive deles: <b> mail.google.com e drive.google.com </b>

Endereço de IP é uma serie de caracteres que é a conversão desse domínio, que é transformada pelo DNS <b> (Domain Name System). </b> então quando digitamos www.google.com
O nosso DNS procura no seu banco de dados o seu IP e acessa algo do tipo assim: 192.203.232.332 por baixo dos panos.

Existe mais algo interessante que são as portas, imagine que seu servidor é uma casa e você precisa dar acesso ao seu usuário, então normalmente a porta de bem vinda do http é a 80.
se você for entrar em qualquer site comum com a porta: <b>wwww.google.com.br:80</b> vai ver que vai entrar tranquilamente, já para o https é usado a partoda 443, você que configura qual porta
a sua aplicação vai ficar disponível para os usuários, além disso existem outros protocolos que definem a sua porta padrão como por exemplo o FTP que usa 21 ou SSH que usa 22.

Por último e não menos importante vamos falar sobre caminhos e recursos, são basicamentes descrições para chegar ao um determinado ponto na url por exemplo:
www.alura.com.br/noje-js-curso -> <b>node-js-curso</b> é um recurso, mas podemos ter casos de  caminhos com recursos como
wwww.alura.com.br/cursos/front-end -> <b> cursos é o caminho e front-end é o recurso final</b>

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/http-url.png)


# URL VS URI

<b>URI (Uniform Resource Identifier) e URL(Uniform Resource Locator) </b> É basicamente a definição para os endereços que digitamos, a maior diferença é que toda URI é uma URI, mas nem toda 
URL, é uma URI, já que URI pode determinar uma URL com um recurso específico.
E agora existe mais um chamado: <b> URN (Uniform Resource Name). </b> que é um padrão mais claro e bem feito

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/http-uri-urn-url.png)

# Sessões E Stateless e Cookies

Sessões: é o tempo usado pelo o cliente em uma determinada aplicação

Toda requisição HTTP é stateless ou seja elas são independentes e contém todos os dados necessários de forma que não tem como ver o que tinha na passada por outra requisição.

Quando efetuamos o login em uma aplicação, enviamos nossos dados secretos, o servidor do outro lado irá gerar uma senha um código aleatório que dura alguns momentos, e ele ficará sendo usado
em nossas próximas requisições evitando que a gente fique passando dados sensíveis em cada requisição que precisa de password e login, segue um exemplo abaixo.

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/alura-req-res-cookie.png)

Esses códigos são guardados em nossos <b> COOKIES </b> basicamente é um espaço no navegador que podemos armazenar algumas informações e ficar reutilizando de maneira segura nas nossas páginas de acesso, exemplo de como são guardados os cookies logo abaixo:

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/alura-cookie-navegador.png)

O HTTP usa sessões para salvar informações do usuário
Sessões só são possíveis por uso de Cookies
Cookies são pequenos arquivos que guardam informações no navegador
O HTTP é stateless, não mantem estado.

# Status HTTP

Por padrão os Status HTTP possuem tipos de respostas diferentes iniciais para comportamentos mapeados

![Ilustração protocolo](https://s3.amazonaws.com/caelum-online-public/http/classe-http-2.png)

Sempre que uma requisição receber 301 como status que significa: <b> Moved Permanently </b>, esse response precisa vir com uma <b> Location </b> justamente com o novo endereço para ser redirecionado
para a nova página.

# Parâmetros na requisição

A forma de passar parâmetros por uma requisição é bem simples, eles se chamam de Query Params, eles são enviados pela URL, basta adicionar o <b> ? </b> dps de todo recurso da url
e juntar com o que você deseja enviar, no exemplo abaixo enviamos o parâmetro novoParam passando o valor: nodeJs

https://www.bb.com.br/curso?novoParam=nodeJs

Caso você queira enviar mais parâmetros só precisa adicionar o <b> & </b> da seguinte forma:

https://www.bb.com.br/curso?novoParam=nodeJs&data=20-02-03

Outro ponto interessante é  que não usamos esse método para enviar dados seguros como senhas ou informações secretas, para isso enviamos atravé do método <b>POST </b> pelo body ( CORPO ) da requisição.