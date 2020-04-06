---
title: Visualizador da Biblioteca de Imagens | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707742"
---
# <a name="image-library-viewer"></a>Visualizador da biblioteca de imagens
A ferramenta Visual Studio Image Library Viewer pode carregar e pesquisar manifestos de imagem, permitindo que o usuário os manipule da mesma forma que o Visual Studio faria. O usuário pode alterar o plano de fundo, tamanhos, DPI, alto contraste e outras configurações. A ferramenta também exibe informações de carregamento para cada manifesto de imagem e exibe informações de origem para cada imagem no manifesto da imagem. Esta ferramenta é útil para:

1. Diagnóstico de erros

2. Garantir que os atributos sejam definidos corretamente em manifestos de imagem personalizados

3. Procurando imagens no Catálogo de Imagens do Visual Studio para que uma extensão do Visual Studio possa usar imagens que se encaixem no estilo do Visual Studio

   ![Herói do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-hero.png "Herói do visualizador da biblioteca de imagens")

   **Apelido de imagem**

   Um apelido de imagem (ou apelido para abreviar) é um par GUID:ID que identifica exclusivamente um ativo de imagem ou lista de imagens na Biblioteca de Imagens.

   **Arquivos manifestos de imagem**

   Os arquivos manifestos de imagem (.imagemanifest) são arquivos XML que definem um conjunto de ativos de imagem, os apelidos que representam esses ativos e a imagem real ou imagens que representam cada ativo. Os manifestos de imagem podem definir imagens independentes ou listas de imagens para suporte à ui legado. Além disso, existem atributos que podem ser definidos no ativo ou nas imagens individuais por trás de cada ativo para mudar quando e como esses ativos são exibidos.

   **Esquema de manifesto de imagem**

   Um manifesto de imagem completo se parece com isso:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Símbolos**

 Como um auxílio de legibilidade e manutenção, o manifesto de imagem pode usar símbolos para valores de atributo. Os símbolos são definidos assim:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Subelemento**|**Definição**|
|Importar|Importa os símbolos do arquivo manifesto dado para uso no manifesto atual.|
|Guid|O símbolo representa um GUID e deve corresponder à formatação GUID.|
|ID|O símbolo representa um ID e deve ser um inteiro não negativo.|
|String|O símbolo representa um valor de corda arbitrário.|

 Os símbolos são sensíveis a maiúsculas e outras referências usando a sintaxe de $(nome símbolo):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Alguns símbolos são predefinidos para todos os manifestos. Estes podem ser usados \<no atributo Uri do elemento> Fonte ou \<Importação> para referenciar caminhos na máquina local.

|||
|-|-|
|**Símbolo**|**Descrição**|
|CommonProgramFiles|O valor da variável ambiente %CommonProgramFiles%|
|LocalAppData|O valor da variável ambiente %LocalAppData%|
|Pasta de manifesto|A pasta contendo o arquivo manifesto|
|Mydocuments|O caminho completo da pasta Meus documentos do usuário atual|
|ProgramFiles|O valor da variável ambiente %ProgramFiles%|
|Sistema|A pasta Windows\System32|
|Windir|O valor da variável ambiente %WinDir%|

 **Imagem**

 O \<elemento Imagem> define uma imagem que pode ser referenciada por um apelido. O GUID e o ID juntos formam o apelido da imagem. O apelido para a imagem deve ser único em toda a biblioteca de imagens. Se mais de uma imagem tem um nome dado, a primeira encontrada durante a construção da biblioteca é a que é retida.

 Deve conter pelo menos uma fonte. Embora fontes neutras de tamanho darão os melhores resultados em uma ampla gama de tamanhos, eles não são necessários. Se o serviço for solicitado para uma imagem \<de um tamanho não definido no elemento Imagem> e não houver uma fonte neutra de tamanho, o serviço escolherá a melhor fonte específica de tamanho e dimensionará-a para o tamanho solicitado.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Guid|[Necessário] A parte GUID do apelido de imagem|
|ID|[Necessário] A parte de ID do apelido de imagem|
|Inversão de cores permitida|[Opcional, padrão verdadeiro] Indica se a imagem pode ter suas cores programáticamente invertidas quando usada em um fundo escuro.|

 **Fonte**

 O \<elemento Source> define um único recurso de fonte de imagem (XAML e PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Uri|[Necessário] Um URI que define de onde a imagem pode ser carregada. Pode ser um dos seguintes:<br /><br /> - Um [Pacote URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) usando a autoridade application:///<br /><br /> - Uma referência absoluta de recursos componentes<br /><br /> - Um caminho para um arquivo contendo um recurso nativo|
|Segundo plano|[Opcional] Indica o que em tipo de fundo a fonte deve ser usada.<br /><br /> Pode ser um dos seguintes:<br /><br /> - *Luz*: A fonte pode ser usada em um fundo leve.<br /><br /> - *Escuro*: A fonte pode ser usada em um fundo escuro.<br /><br /> - *HighContrast*: A fonte pode ser usada em qualquer plano de fundo no modo High Contrast.<br /><br /> - *HighContrastLight*: A fonte pode ser usada em um fundo leve no modo High Contrast.<br /><br /> -*HighContrastDark*: A fonte pode ser usada em um fundo escuro no modo High Contrast.<br /><br /> Se o atributo **Fundo** for omitido, a fonte poderá ser usada em qualquer plano de fundo.<br /><br /> Se **O fundo** é *claro,* *escuro,* *highcontrastlight*ou *highcontrastdark,* as cores da fonte nunca são invertidas. Se **O Fundo de Fundo** for omitido ou definido como *HighContrast,* a inversão das cores da fonte será controlada pelo atributo **AllowColorInversion** da imagem.|

 Um \<elemento> Fonte pode ter exatamente um dos seguintes subelementos opcionais:

||||
|-|-|-|
|**Elemento**|**Atributos (todos necessários)**|**Definição**|
|\<tamanho>|Valor|A fonte será usada para imagens do tamanho dado (em unidades do dispositivo). A imagem será quadrada.|
|\<tamanho>|MinSize|A fonte será usada para imagens de MinSize a MaxSize (em unidades de dispositivos) inclusivamente. A imagem será quadrada.|
|\<Dimensões>|Largura, Altura|A fonte será usada para imagens da largura e altura dada (em unidades do dispositivo).|
|\<> dimensionrange|MinWidth, MinHeight,<br /><br /> Largura máxima, MaxHeight|A fonte será usada para imagens desde a largura/altura mínima até a largura/altura máxima (em unidades do dispositivo) inclusivamente.|

 Um \<elemento> fonte também \<pode ter um subelemento \<de> nativo opcional, que define uma fonte> que é carregada a partir de um conjunto nativo em vez de um conjunto gerenciado.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atributo**|**Definição**|
|Type|[Necessário] O tipo de recurso nativo, xaml ou PNG|
|ID|[Necessário] A parte de ID inteiro do recurso nativo|

 **Imagelist**

 O \<elemento ImageList> define uma coleção de imagens que podem ser devolvidas em uma única tira. A tira é construída sob demanda, conforme necessário.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Guid|[Necessário] A parte GUID do apelido de imagem|
|ID|[Necessário] A parte de ID do apelido de imagem|
|Externo|[Opcional, padrão falso] Indica se o apelido da imagem faz referência a uma imagem no manifesto atual.|

 O apelido para a imagem contida não precisa fazer referência a uma imagem definida no manifesto atual. Se a imagem contida não puder ser encontrada na biblioteca de imagens, uma imagem de espaço reservado em branco será usada em seu lugar.

## <a name="how-to-use-the-tool"></a>Como usar a ferramenta
 **Validando um manifesto de imagem personalizado**

 Para criar um manifesto personalizado, recomendamos que você use a ferramenta ManifestFromResources para gerar automaticamente o manifesto. Para validar o manifesto personalizado, inicie o Visualizador da Biblioteca de Imagens e selecione > Defina caminhos... para abrir a caixa de diálogo Diretórios de pesquisa. A ferramenta usará os diretórios de pesquisa para carregar manifestos de imagem, mas também os usará para encontrar os arquivos .dll que contêm as imagens em um manifesto, por isso certifique-se de incluir os diretórios manifesto e DLL nesta caixa de diálogo.

 ![Pesquisa do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-search.png "Pesquisa do visualizador da biblioteca de imagens")

 Clique **em Adicionar...** para selecionar novos diretórios de pesquisa para procurar manifestos e seus DLLs correspondentes. A ferramenta lembrará desses diretórios de pesquisa, e eles podem ser ligados ou desligados verificando ou desverificando um diretório.

 Por padrão, a ferramenta tentará encontrar o diretório de instalação do Visual Studio e adicionar esses diretórios à lista de diretórios de pesquisa. Você pode adicionar manualmente diretórios que a ferramenta não encontra.

 Uma vez que todos os manifestos são carregados, a ferramenta pode ser usada para alternar cores **de fundo,** **DPI,** **alto contraste**ou **acinzentado** para as imagens para que o usuário possa inspecionar visualmente os ativos de imagem para verificar se eles estão sendo renderizados corretamente para várias configurações.

 ![Fundo do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-background.png "Fundo do visualizador da biblioteca de imagens")

 A cor de fundo pode ser definida como Luz, Escuro ou um valor personalizado. A seleção de "Cor personalizada" abrirá uma caixa de diálogo de seleção de cores e adicionará essa cor personalizada à parte inferior da caixa de combinação de fundo para fácil recordação mais tarde.

 ![Cor personalizada do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-custom-color.png "Cor personalizada do visualizador da biblioteca de imagens")

 Selecionar um apelido de imagem exibe as informações para cada imagem real por trás desse apelido no painel Detalhes da imagem à direita. O painel também permite que os usuários copiem um apelido pelo nome ou pelo valor bruto GUID:ID.

 ![Detalhes da imagem do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-image-details.png "Detalhes da imagem do visualizador da biblioteca de imagens")

 As informações exibidas para cada fonte de imagem incluem que tipo de plano de fundo exibi-lo, se pode ser temático ou suporta Alto Contraste, para quais tamanhos é válido ou se é neutro em tamanho e se a imagem vem de uma montagem nativa.

 ![Espectador da biblioteca de imagens pode tema](../../extensibility/internals/media/image-library-viewer-can-theme.png "Espectador da biblioteca de imagens pode tema")

 Ao validar um manifesto de imagem, recomendamos que você implante o DLL manifesto e de imagem em suas localizações reais. Isso verificará se quaisquer caminhos relativos estão funcionando corretamente e que a biblioteca de imagens pode encontrar e carregar o manifesto e a DLL de imagem.

 **Procurando por catálogo de imagens KnownMonikers**

 Para melhor combinar com o estilo visual studio, uma extensão do Visual Studio pode usar imagens no Visual Studio Image Catalog em vez de criar e usar o seu próprio. Isso tem o benefício de não ter que manter essas imagens, e garante que a imagem terá uma imagem de suporte de alta DPI, por isso deve parecer correta em todas as configurações de DPI que o Visual Studio suporta.

 O visualizador da biblioteca de imagens permite que um manifesto seja pesquisado para que um usuário possa encontrar o apelido que representa um ativo de imagem e usar esse apelido em código. Para procurar imagens, digite o termo de pesquisa desejado na caixa de pesquisa e pressione Enter. A barra de status na parte inferior exibirá quantas correspondências foram encontradas fora do total de imagens em todos os manifestos.

 ![Filtro de visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro de visualizador da biblioteca de imagens")

 Ao procurar apelidos de imagem em manifestos existentes, recomendamos que você procure e use apenas os apelidos do Visual Studio Image Catalog, outros apelidos intencionalmente acessíveis ao público ou seus próprios apelidos personalizados. Se você usar apelidos não públicos, a ui personalizada pode ser quebrada ou ter suas imagens alteradas de maneiras inesperadas se ou quando esses apelidos e imagens não públicas forem alterados ou atualizados.

 Além disso, a busca por GUID é possível. Este tipo de pesquisa é útil para filtrar a lista para um único manifesto, ou subseção única de um manifesto se esse manifesto contiver vários GUIDs.

 ![Guia do filtro do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Guia do filtro do visualizador da biblioteca de imagens")

 Finalmente, a busca por ID também é possível.

 ![ID do filtro do visualizador da biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID do filtro do visualizador da biblioteca de imagens")

## <a name="notes"></a>Observações

- Por padrão, a ferramenta puxará vários manifestos de imagem presentes no diretório de instalação do Visual Studio. O único que tem apelidos de consumo público é o manifesto **Microsoft.VisualStudio.ImageCatalog.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 **(não** anular este GUID em um manifesto personalizado) Tipo: KnownMonikers

- A ferramenta tenta o lançamento para carregar todas as manifestações de imagem que encontra, então pode levar vários segundos para que o aplicativo realmente apareça. Também pode ser lento ou não durante o carregamento dos manifestos.

## <a name="sample-output"></a>Saída de exemplo
 Esta ferramenta não gera nenhuma saída.
