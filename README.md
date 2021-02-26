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