<h1 align=center>Permissões e Sensores</h1>

<h3 align="center">Integrantes: Gustavo Henrique da Silva Souza e Guilherme Sola Gárcia</h3>
<br>
<p align=center>		
Esta atividade envolve pesquisar e fornecer explicações simples sobre os seguintes tópicos:

- Identifique as principais permissões necessárias para acessar recursos específicos do seu dispositivo móvel, como câmera, localização e contatos.

- Explorar as ações utilizadas nas intenções implícitas, descrevendo os seus tipos e utilizações em aplicações móveis.

- Analisar os sensores disponíveis nos dispositivos móveis, explicar a sua finalidade e mencionar o tipo de dados fornecidos por cada sensor.

Essas informações são essenciais para que os desenvolvedores de aplicativos móveis entendam como interagir com dispositivos e sistemas operacionais de maneira eficaz e segura.
</p>

<details>
   <summary><h1>Introdução</h1></summary>
    <p>	
Nesta atividade apresentaremos as principais permissões em dispositivos móveis, explicaremos as “ações” utilizadas nas intenções implícitas e exploraremos os sensores disponíveis, incluindo sua finalidade e tipos de retorno. Vamos aprofundar nossa compreensão de como esses elementos se relacionam com o desenvolvimento de aplicativos e experiências móveis.
    </p>
</details>


<details>
    <summary><h1>Permissões Essenciais e Seus Destinos de Uso</h1></summary>
   <Li align =justify><strong>1. Permissão de Localização:</strong>
	(android.permission.ACCESS_FINE_LOCATION e android.permission.ACCESS_COARSE_LOCATION):

Essa permissão é necessária para que o aplicativo consiga acessar informações de localização do dispositivo, como GPS e torres de celular. Ela é muito utilizada em aplicativos de navegação como o Waze e o Google Maps.
  </li>
  <br>

  <Li align =justify><strong>2. Permissão de Câmera (android.permission.CAMERA):</strong>
	  Essa permissão é necessária para que o aplicativo consiga tirar fotos, gravar vídeos, fazer videochamadas. Essa permissão é mais utilizado como aplicativos como o Instagram e Whatsapp.
  </Li>
  <br>


  <Li align =justify><strong>3. Permissão de Armazenamento (android.permission.READ_EXTERNAL_STORAGE e android.permission.WRITE_EXTERNAL_STORAGE):</strong>
	  Essa permissão é necessária para que o aplicativo consiga ter acesso e salvar documentos, fotos e arquivos no dispositivo do usuário.
  </Li>
  <br>


   <Li align =justify><strong>4. Permissão de Microfone (android.permission.RECORD_AUDIO): </strong>
   	Essa permissão é usada para que o aplicativo tenha acesso ao microfone do usuário, utilizado para gravar áudios, chamadas de voz ou até reconhecimento de fala.
   </Li>
   <br>

 <Li align =justify><strong>5. Permissão de Contatos (android.permission.READ_CONTACTS e android.permission.WRITE_CONTACTS):</strong>
   	Essa permissão garante acesso do aplicativo aos contatos salvos no dispositivo do usuário além de conseguir salvar novos contatos.
   </Li>
   <br>

   <Li align =justify><strong>6. Permissão de Telefone (android.permission.CALL_PHONE):
</strong>
  	
É utilizada para que o aplicativo consiga executar chamadas telefônicas a partir do dispositivo usado.
   </Li>
</details>

<details>
    <summary><h1>Tipos de Intents e Suas Finalidades</h1></summary>
	<Li align =justify><strong>Intent Explicita:</strong> 
		Intents explícitas são a maneira precisa de conduzir a ação desejada em um dispositivo Android. Eles especificam qual aplicativo será responsável por tratar a intent e fornecem informações como o nome do pacote do aplicativo de destino ou o nome completo da classe do componente. Normalmente, intents explícitas são usadas para lançar componentes dentro do próprio aplicativo, uma vez que sabemos o nome da classe da atividade ou serviço que queremos lançar. Um exemplo prático é quando você deseja iniciar uma nova atividade em resposta a uma ação do usuário, como abrir uma tela de configurações após clicar em um botão específico. Outra aplicação comum é iniciar um serviço para realizar tarefas em segundo plano, como baixar arquivos, sem exigir interação direta do usuário. O uso eficaz de intents explícitas é crucial para o desenvolvimento de aplicativos Android, pois permite identificar as ações necessárias, melhorando a experiência do usuário e garantindo que seu aplicativo funcione de maneira suave e eficiente.
	</Li>
	<br>

 	
  
<Li align =justify><strong>Intent Implícita:</strong>
  	As Intents implícitas têm a característica de não estarem vinculadas a um componente específico, mas sim declarar uma ação geral a ser executada, o que permite que um componente de outra aplicação a trate. Isso proporciona flexibilidade significativa ao ecossistema Android, pois diferentes aplicativos podem responder ao mesmo tipo de intent implícita, proporcionando uma experiência de usuário rica e integrada. Por exemplo, se você quiser exibir um local em um mapa para o usuário, poderá usar uma intent implícita para solicitar que um aplicativo compatível com mapas (como o Google Maps) renderize e exiba um local específico no mapa. Isso significa que você não precisa desenvolver funcionalidades de mapeamento internamente, economizando tempo e recursos e permitindo que os usuários escolham seu aplicativo de mapeamento preferido. As intents implícitas são um componente comum da arquitetura Android que facilita a interação entre aplicativos e promove a reutilização de funcionalidades entre aplicativos, isso aumenta a experiência do usuário e reduz o desenvolvimento de aplicativos mais eficazes e completos.
</Li>
<br>

<Li align =justify><strong>Exemplos de Intens:</strong>
Aqui estão alguns exemplos de como fazer uma intent explicita e implícita

	
 <h2><strong>Intent Explicita:</strong></h2>

 <h3><strong>Kotlin</strong></h3>
	// Executed in an Activity, so 'this' is the Context
// The fileUrl is a string URL, such as "http://www.example.com/image.png"
val downloadIntent = Intent(this, DownloadService::class.java).apply {
    data = Uri.parse(fileUrl)
}
startService(downloadIntent)
<br>

<h3><strong>Java</strong></h3>
// Executed in an Activity, so 'this' is the Context
// The fileUrl is a string URL, such as "http://www.example.com/image.png"
Intent downloadIntent = new Intent(this, DownloadService.class);
downloadIntent.setData(Uri.parse(fileUrl));
startService(downloadIntent);
<br>


 <h2><strong>Intent Implícita:</strong></h2>

 <h3><strong>Kotlin</strong></h3>
 // Create the text message with a string
val sendIntent = Intent().apply {
    action = Intent.ACTION_SEND
    putExtra(Intent.EXTRA_TEXT, textMessage)
    type = "text/plain"
}

// Verify that the intent will resolve to an activity
if (sendIntent.resolveActivity(packageManager) != null) {
    startActivity(sendIntent)
}
<br>

<h3><strong>Java</strong></h3>
// Create the text message with a string
Intent sendIntent = new Intent();
sendIntent.setAction(Intent.ACTION_SEND);
sendIntent.putExtra(Intent.EXTRA_TEXT, textMessage);
sendIntent.setType("text/plain");

// Verify that the intent will resolve to an activity
if (sendIntent.resolveActivity(getPackageManager()) != null) {
    startActivity(sendIntent);
}
</Li>

</details>

<details>
		<summary><h1>Sensores de Movimento e Ambiente em Dispositivos</h1></summary>
	<li align=justify><strong>
Sensor: TYPE_ACCELEROMETER</strong> Descrição: Mede a força de aceleração em m/s² nos três eixos físicos (x, y, z), incluindo a gravidade.  
Valores Usados: Detecção de movimento (agitação, inclinação, etc.).
        </li>
	<br>
 
 <Li align=justify><strong>Sensor: TYPE_AMBIENT_TEMPERATURE</strong>  Descrição: Mede a temperatura ambiente em °C.  
Valores Usados: Monitoramento das temperaturas do ar.
 </Li>
	<br>
	
<Li align=justify><strong>Sensor: TYPE_GRAVITY</strong>  Descrição: Mede a força da gravidade em m/s² nos três eixos físicos (x, y, z).  
Valores Usados: Detecção de movimento (agitação, inclinação, etc.).
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_GYROSCOPE</strong>  Descrição: Mede a taxa de rotação em rad/s em torno dos três eixos físicos (x, y, z).  
Valores Usados: Detecção de rotação (giro, volta, etc.).
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_LIGHT</strong>  Descrição: Mede o nível de luz ambiente em lx.  
Valores Usados: Controle do brilho da tela.
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_LINEAR_ACCELERATION</strong>  Descrição: Mede a força de aceleração em m/s² nos três eixos físicos (x, y, z), excluindo a gravidade.  
Valores Usados: Monitoramento da aceleração em um único eixo.

</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_MAGNETIC_FIELD</strong>  Descrição: Mede o campo geomagnético para os três eixos físicos (x, y, z) em μT.  
Valores Usados: Criação de uma bússola.
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_ORIENTATION </strong>  Descrição: Mede os graus de rotação em torno dos três eixos físicos (x, y, z).  
Valores Usados: Determinação da posição do dispositivo.
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_PRESSURE</strong>   Descrição: Mede a pressão do ar ambiente em hPa ou mbar.  
Valores Usados: Monitoramento das mudanças na pressão do ar.

</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_PROXIMITY</strong>  Descrição: Mede a proximidade de um objeto em cm com relação à tela de um dispositivo.  
Valores Usados: Posição do smartphone durante uma chamada.
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_RELATIVE_HUMIDITY </strong>  Descrição: Mede a umidade relativa do ar em %.  
Valores Usados: Monitoramento de ponto de condensação, umidade absoluta e relativa.

</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_ROTATION_VECTOR</strong>  Descrição: Mede a orientação do dispositivo através do vetor de rotação.  
Valores Usados: Detecção de movimento e de rotação.
</Li>
<br>

<Li align=justify><strong>Sensor: TYPE_TEMPERATURE</strong>  Descrição: Mede a temperatura do dispositivo em °C (substituído por TYPE_AMBIENT_TEMPERATURE na API nível 14).  
Valores Usados: Monitoramento de temperaturas.
</Li>
<br>

</details>

<details>
	<summary><h1>Conclusão</h1></summary>
	<p>
		Em resumo, as permissões, intents e sensores desempenham papéis cruciais no desenvolvimento de aplicativos Android. Permissões garantem acesso controlado a recursos do dispositivo, intents proporcionam ações precisas e integração entre aplicativos, enquanto sensores permitem interação adaptativa ao ambiente físico. Compreender e aplicar esses elementos é essencial para criar aplicativos responsáveis, inovadores e centrados no usuário, promovendo uma experiência mais segura e personalizada.
	</p>
	

</details>


<details>
	<summary><h1>Fontes Usadas</h1></summary>
	<p>
	Aqui estão as fontes ultilizadas para fazer a realização da pesquisa:
		<br>
		https://developer.android.com/guide/components/intents-filters?hl=pt-br#Types
		<br>
		https://mariovalney.com/aula-10-como-mudar-de-activity-com-intents/
		<br>
		https://developer.android.com/guide/topics/sensors/sensors_overview?hl=pt-br
		https://www.tudocelular.com/curiosidade/noticias/n148775/dica-tutorial-defina-permissoes-apps-android.html#:~:text=Confira%20abaixo%20a%20lista%20de,alterar%20seu%20hist%C3%B3rico%20de%20chamadas
	</p>
	

</details>



