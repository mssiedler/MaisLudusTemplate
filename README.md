# +Ludus Template

Template Unity com ênfase na criação de Apps estilo Drag and Drop voltado a crianças e seguindo preceitos de Tecnologia Assististiva.

Criado a partir do projeto [+Ludus](https://linktr.ee/maisludus), Projeto de Inovação Tecnológica que visa a criação e disponibilização de aplicativos inclusivos, com ênfase em crianças com TEA.

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

# Instalação

1) Baixar o arquivo **com.ludus.template.tgz**

2) Salvar na pasta **C:\Program Files\Unity\Hub\Editor\2022.3.13f1\Editor\Data\Resources\PackageManager\ProjectTemplates ou equivalente (dependendo do Sistema Operacional e/ou versão da Unity instalada)**.

3) Preferencialmente, instalar a versão 2022.3.13f1 e reiniciar o Unity Hub

4) Criar um novo Projeto, ir na versão 2022.3.13f1,  e selecionar o template +Ludus conforme a imagem.

![Imagem da criação do novo Projeto com o template +Ludus](http://aplicativoseducacionais.epizy.com/readmeMedia/instalacao.png)


5) No novo projeto, verificar se as pastas foram adequadamente geradas conforme o exemplo.

![Estrutura de Pastas](http://aplicativoseducacionais.epizy.com/readmeMedia/pastas.png)


# Funcionamento

O Template consiste em criar fases estilo *Drag and Drop* a partir de imagens e sons pré estabelecidos.

O Template oferece a possibilidade de apoias a criação de Aplicativos sem a necessidade de codificação da lógica das fases em que o Drag and Drop é utilizado. É possível, usando os prefabs disponibilizados e o *Inspector* da Unity, configurar as fases e utilizar os recursos desenvolvidos para apoiar a criação de Aplicativos. 

Além da codificação, é possível utilizar as *GUI* desenvolvidas a partir dos preceitos de interface avaliados no projeto +Ludus. Nessa GUI são apresentadas telas e botões que podem ser utilizadas e customizadas conforma a necessidade do App desenvolvido.


# Configuração

Para utilização correta do *Template*, a primeira etapa consiste na elaboração dos *Assets* necessários para criação das fases. 

O **+Ludus Template** funciona a partir da correta elaboração das imagens e sons que serão utilizadas na elaboração das fases. Basicamente uma fase apresenta os seguintes elementos apresentados na imagem a seguir.

![Imagem exemplo da Fase](http://aplicativoseducacionais.epizy.com/readmeMedia/instalacao.png)

Nessa imagem é apresentada a direita o que é chamado de objetos do jogo(no caso o ET e a Nave) e a esqueda as respectivas sombras objetos. 

Para utilização do Template é necessário que as imagens desses objetos, bem como suas sombras estejam organizados de forma que o Template possa identifica-los e realizar corretamente o carregamento da fase. Para isso será apresentado a seguir o passo a passo para criação e organização do material da fase.

## Estrutura de Arquivos e Pastas

O Template apresenta a seguinte estrutura de disposição de pastas: 

```
  - Assets
    -- Resources
        ---fases 
```

A partir da pasta **fases**, o usuário deve organizar em pasta específica os *assets* que serão utilizados no aplicativo. No template são apresentadas duas pastas que servem de exemplo, **exemplo** e **teste**, com as seguintes estruturas de arquivo:


```
  - Assets
    -- Resources
        ---fases 
            ----teste
                objeto.png
                sombra.png
                ----- objetosons
                        audio_0, audio_1, audio_2, audio_3
            ----exemplo
                auxiliar.png
                objeto.png
                sombra.png
                objetoPareado.png
                ----- auxiliarsons
                        audio_0, audio_1, audio_2, audio_3, audio_4, audio_5, audio_6, audio_7
                ----- objetosons
                        audio_0, audio_1, audio_2, audio_3, audio_4, audio_5, audio_6, audio_7

```


A pasta **teste** apresenta a configuração básica para utilização do template, com os arquivos necessário para realizar o Drag and Drop com apoio de áudio quando o usuário clica no objeto que deseja parear. Então vamos ao passo a passo para criar o material a ser utilizado em uma nova fase pelo usuário.

### Passo a Passo para criação de uma nova fase 

1) Criar uma nova pasta dentro da pasta **fases**.
2) Importar o *SpriteSheet* com os objetos a serem pareados e renomea-lo para **objeto**.
3) "Fatiar" o Sprite para este fique múltiplo (usar o Sprite Editor).
4) Importar o *SpriteSheet* com as sombras dos ojetos e renomea-lo para **sombra**
5) "Fatiar" o Sprite para este fique múltiplo (usar o Sprite Editor).
6) Criar uma pasta chamada **objetosons** e inserir adicionar na pasta os arquivos de áudo relacionados a cada objeto que pode ser pareado.
7) Renomear os arquivos de áudio para corresponder a cada objeto da fase. Essa correspondencia se dá pela ordem em que os objetos aparecem no SpriteSheet. O áudio relacionado ao primeiro objeto deve ser renomeado para audio_0, o segundo audio_1 e assim sucessivamente.

Como exemplo vamos analisar os arquivos que apresentam os *SpriteSheets* da pasta **teste** que vem no Template.

![Imagem exemplo da Fase](http://aplicativoseducacionais.epizy.com/readmeMedia/sprites.png)


A primeia observação importante é que, tanto o o objeto quanto a sombra apresentam as imagens na **mesma ordem** e com correspondencia de tamanho entre os objetos e as sombras para uma correta sobreposição.

No caso dos áudios é só seguir a ordem dos objetos apresentados, ou seja, o arquivo *audio_0* corresponde a imagem do ET, *audio_1* corresponde a imagem do planeta Terra, e assim por diante.

## Layout 

O template oferece orientação Vertical ou Horizontal para a representação das fases. 
Quanto a forma de pareamento (implementação do Drag and Drop) estes podem ser feitos no formato **N pra N**, onde existe uma sombra para cada objeto, ou **N pra 1**, com uma sombra apenas e o usuário deve parear corretamente a sombra que corresponde ao objeto a ser pareado.

Considerando os prefabs existes na pasta *Assets/Resources/preFabs/Paineis*, o desenvolvedor pode optar pelos seguintes elementos:

* **H1**: orientação horizontal e *N pra 1*;
* **HN**: orientação horizontal e *N pra N*;
* **V1**: orientação vertical e *N pra 1*; e
* **VN**: orientação vertical e *N pra N*;


### Exemplo de utilização

Suponto uma aplicação cuja fase será horizontal com todos objetos sendo pareados para suas respectivas sombras e com a seguinte configuração:

* Assets adicionados na pasta **teste**.
* A fase devera apresentar duas vezes um elemento para parear, duas vezes dois elementos para parear e, por fim, uma vez quatro elementos para parear.
* Quando terminar a fase, a Cena chamada *FinalCode* deve ser chamada.

Vamos ao passo a passo:

1) Criar uma nova Cena chamada Tutorial.

2) Arrastar o preFab correspondente a configuração desejada. No caso do exemplo, é Horizontal e com todos objetos pareados, o que sugere o preFab **HN**.

3) Arraste a Camera principal ao Canvas do prefab.


> Se der PLAY na Cena Tutorial ele deve exibir a imagem semelhante a apresentada a  seguir, com um objeto e uma sombra. Isso se deve ao preFab ja vir com uma configuração inicial para que o desenvolvedor possa ver o jogo rodando. 



Agora faremos a adaptação do prefab conforme colocado na especificação do exemplo. 
Deve ser definida a pasta na qual os assets estão inseridos (no nosso caso **teste**, a configuração dos níveis e, por fim, definir o nome da cena final, que foi especificada como **FinalCode** que é uma cena quem vem no pacote de exemplos do Template).

Essa configuração é feita no Script do Painel do prefab e é feita ajustando os parâmetros conforme a necessidade da Aplicação conforme apresentado a seguir:

![Configuração do Script](http://aplicativoseducacionais.epizy.com/readmeMedia/configScript1.png)

Com essa configuração a fase já deve funcionar conforme o esperado.

> Checar se a pasta existe, está corretamente configurada, e se a tela final escolhida está corretamente referenciada nas Configurações de compilação (*Build Settings*)

## Configurações Adicionais

O Template oferece algumas customizações que podem auxiliar o desenvolvedor na criação dos aplicativos. Basicamente é possível colocar um conteúdo auxiliar ao local onde o objeto deve ser pareado e também é possível substituir a imagem do objeto quando ocorre o pareamento. A seguir é apresentado como implementar essas duas funcionalidades.

### Conteúdo Auxiliar

Para adicionar o conteúdo auxiliar, o primeiro passo é realizar a configuração dos Assets. O *SpriteSheet* chamado **auxiliar** é obrigatório, e o material de áudio auxiliar, que é emitido toda vez que o conteúdo auxiliar é clicado, é opcional.

Considerando a pasta teste, se quisermos adicionar um conteúdo auxiliar a estrutura de diretórios ficaria assim:


```
  -teste
    auxiliar.png
    objeto.png
    sombra.png
    -- auxiliarsons
            audio_0, audio_1, audio_2, audio_3
    -- objetosons
            audio_0, audio_1, audio_2, audio_3

```

De novo, é adicionado o arquivo **auxiliar.png** e a pasta **auxiliarsons**, com os áudios do conteúdo auxiliar.

#### Exemplo de utilização

Para exemplificar a utilização do conteúdo auxiliar usaremos a fase **exemplo** que vem no template. Inicialmente vamos ver como fica a fase sem o conteúdo auxiliar.


A fase exemplo consiste em um balde "pintar" a sombra. Nesse caso é fundamental ter o conteúdo auxiliar, pois sem ele não tem como saber como pintar cada quadrado. 
Para habilitar o conteúdo auxiliar é necessário apenas habilitar a caixa de seleção conforme a imagem a seguir.

Após marcar o conteúdo a apresentação do conteúdo fica da seguinte forma:

### Customização do conteúdo auxiliar

O Template, por padrão, utiliza o prefab **sombraComAuxiliar** para exibir o conteúdo na cena. Esse prefab coloca o conteúdo a direita da sombra onde ocorrerá o pareamento. 

Caso o usuário queria alterar esse posicionamento, o recomendável é clonar o prefab  **sombraComAuxiliar**, realizar as alterações desejadas e referenciar no script o prefab alterado.

#### Exemplo de utilização 

Primeiramente criamos um novo prefab, clonado a partir do  **sombraComAuxiliar**, que chamaremos de **auxiliarBaixo**. Na figura a seguir é apresentado como ficou o novo preFab.

>É importante não mudar nome, hierarquia e quantidade de elementos no novo preFab. O template está apto apenas a mudanças de tamanho e posicionamento.

Para adicionar na Cena o novo auxliar basta mudar o nome do prefab na propriedade **Sombraauxiliar** do script de Layout.

No exemplo a seguir vemos a fase rodando com o novo preFab.


>Como optamos por colocar o conteúdo auxliar embaixo da sombra foi necessário aumentar o painel da sombra. O desenvolvedor tem liberade para customizar o layout do conteúdo apresentado conforme a necessidade da aplicação.


### Substituir ao parear

Essa opção serve para, quando acontecer o pareamento, o usuário possa visulaizar uma imagem diferente do objeto que foi arrastado. Para isso é necessário fazer duas coisas. 

Nos Assets, adicionar um *SpriteSheet* chamado **objetoPareado.png** na mesma pasta dos demais Sprites e, da mesma forma que os demais, este deve ser Sprite multiplo, fatiado e com mesma ordem de correspondencia dos demais elementos criados.

#### Exemplo de utilização

Para utilizar basta marcar a opção **Substituir Objeto ao parear** no Script conforme a figura a seguir.

