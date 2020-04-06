---
title: Dentro do editor
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710321"
---
# <a name="inside-the-editor"></a>Dentro do editor

O editor é composto por vários subsistemas diferentes, que são projetados para manter o modelo de texto do editor separado da visualização de texto e da interface do usuário.

Estas seções descrevem diferentes aspectos do editor:

- [Visão geral dos subsistemas](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [O modelo de texto](../extensibility/inside-the-editor.md#the-text-model)

- [A visualização do texto](../extensibility/inside-the-editor.md#the-text-view)

Estas seções descrevem as características do editor:

- [Tags e classificadores](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Adornos](../extensibility/inside-the-editor.md#adornments)

- [Projeção](../extensibility/inside-the-editor.md#projection)

- [Estrutura de tópicos](../extensibility/inside-the-editor.md#outlining)

- [Amarras do mouse](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operações do editor](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Visão geral dos subsistemas

### <a name="text-model-subsystem"></a>Subsistema de modelo de texto

O subsistema modelo de texto é responsável por representar o texto e permitir sua manipulação. O subsistema modelo <xref:Microsoft.VisualStudio.Text.ITextBuffer> de texto contém a interface, que descreve a seqüência de caracteres que deve ser exibida pelo editor. Este texto pode ser modificado, rastreado e manipulado de muitas maneiras. O modelo de texto também fornece tipos para os seguintes aspectos:

- Um serviço que associa texto a arquivos e gerencia a leitura e a escrita no sistema de arquivos.

- Um serviço de diferenciação que encontra as diferenças mínimas entre duas seqüências de objetos.

- Um sistema para descrever o texto em um buffer em termos de subconjuntos do texto em outros buffers.

O subsistema modelo de texto está livre de conceitos de interface do usuário (UI). Por exemplo, não é responsável pela formatação de texto ou layout de texto, e não tem conhecimento de adornos visuais que possam estar associados ao texto.

Os tipos públicos do subsistema de modelo de texto estão contidos no *Microsoft.VisualStudio.Text.Data.dll* e *no Microsoft.VisualStudio.CoreUtility.dll,* que dependem apenas da biblioteca de classes base do .NET Framework e do Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Subsistema de exibição de texto

O subsistema de exibição de texto é responsável pela formatação e exibição do texto. Os tipos neste subsistema são divididos em duas camadas, dependendo se os tipos dependem do Windows Presentation Foundation (WPF). Os tipos mais <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>importantes são e , que controlam o conjunto de linhas de texto que devem ser exibidas, e também o cuidado, a seleção e as facilidades para adornar o texto usando elementos WPF UI. Este subsistema também fornece margens em torno da área de exibição de texto. Essas margens podem ser estendidas e podem conter diferentes tipos de conteúdo e efeitos visuais. Exemplos de margens são displays de número de linha e barras de rolagem.

Os tipos públicos do subsistema de visualização de texto estão contidos no *Microsoft.VisualStudio.Text.UI.dll* e *no Microsoft.VisualStudio.Text.UI.Wpf.dll*. O primeiro conjunto contém os elementos independentes da plataforma, e o segundo contém os elementos específicos do WPF.

### <a name="classification-subsystem"></a>Subsistema de classificação

O subsistema de classificação é responsável por determinar as propriedades da fonte para texto. Um classificador divide o texto em diferentes classes, por exemplo, "palavra-chave" ou "comentário". O mapa do formato de classificação relaciona essas classes com propriedades reais da fonte, por exemplo, "Consolas Azuis 10 pt". Essas informações são usadas pela exibição de texto quando formatar e renderizar texto. A marcação, que é descrita com mais detalhes mais tarde neste tópico, permite que os dados sejam associados a períodos de texto.

Os tipos públicos do subsistema de classificação estão contidos no Microsoft.VisualStudio.Text.Logic.dll, e interagem com os aspectos visuais da classificação, que estão contidos no Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Subsistema de operações

O subsistema de operações define o comportamento do editor. Ele fornece a implementação para comandos de editor do Visual Studio e o sistema de desfazer.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Um olhar mais atento ao modelo de texto e à visualização do texto

### <a name="the-text-model"></a>O modelo de texto

O subsistema modelo de texto consiste em diferentes agrupamentos de tipos de texto. Estes incluem o buffer de texto, instantâneos de texto e intervalos de texto.

#### <a name="text-buffers-and-text-snapshots"></a>Buffers de texto e instantâneos de texto

A <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface representa uma seqüência de caracteres Unicode que são codificados usando UTF-16, que é a codificação usada pelo `String` tipo no Quadro .NET. Um buffer de texto pode ser persistido como um documento do sistema de arquivos, mas isso não é necessário.

O <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> é usado para criar um buffer de texto vazio, ou <xref:System.IO.TextReader>um buffer de texto que é inicializado a partir de uma seqüência ou de . O buffer de texto pode ser persistido no sistema de arquivos como um <xref:Microsoft.VisualStudio.Text.ITextDocument>.

Qualquer segmento pode editar o buffer de texto até <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>que um segmento se apossar do buffer de texto chamando . Depois disso, só esse fio pode realizar edições.

Um buffer de texto pode passar por muitas versões durante sua vida. Uma nova versão é gerada toda vez que o <xref:Microsoft.VisualStudio.Text.ITextSnapshot> buffer é editado, e um imutável representa o conteúdo dessa versão do buffer. Como os instantâneos de texto são imutáveis, você pode acessar um instantâneo de texto em qualquer segmento, sem restrições, mesmo que o buffer de texto que ele representa continue a mudar.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantâneos de texto e linhas de instantâneo de texto

Você pode ver o conteúdo de um instantâneo de texto como uma seqüência de caracteres ou como uma seqüência de linhas. Caracteres e linhas são indexados a partir de zero. Um instantâneo de texto vazio contém zero caracteres e uma linha vazia. Uma linha é delimitada por qualquer seqüência de caracteres de quebra de linha unicode válida, ou pelo início ou fim do buffer. Os caracteres de quebra de linha são explicitamente representados no instantâneo de texto, e as quebras de linha em um instantâneo de texto não têm que ser todas iguais.

> [!NOTE]
> Para obter mais informações sobre caracteres de quebra de linha no editor do Visual Studio, consulte [Codificações e quebras de linha](../ide/encodings-and-line-breaks.md).

Uma linha de texto <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> é representada por um objeto, que pode ser obtido a partir de um instantâneo de texto para um número de linha específico ou para uma posição de caractere específica.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans e NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> representa uma posição de personagem em um instantâneo. A posição é garantida entre zero e o comprimento do instantâneo. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> representa um período de texto em um instantâneo. Sua posição Final é garantida entre zero e o comprimento do instantâneo. O <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> consiste em um <xref:Microsoft.VisualStudio.Text.SnapshotSpan> conjunto de objetos do mesmo instantâneo.

#### <a name="spans-and-normalizedspancollections"></a>Spans e NormalizedSpanCollections

A <xref:Microsoft.VisualStudio.Text.Span> representa um intervalo que pode ser aplicado a um período de texto em um instantâneo de texto. As posições de snapshot são baseadas em zero, então os intervalos podem começar em qualquer posição, incluindo zero. A `End` propriedade de um vão é igual `Start` à `Length` soma de sua propriedade e sua propriedade. A `Span` não inclui o caractere que `End` é indexado pela propriedade. Por exemplo, um período que tem Start=5 e Length=3 tem End=8, e inclui os caracteres nas posições 5, 6 e 7. A notação para este período é [5..8).

Dois vãos se cruzam se tiverem alguma posição em comum, incluindo a posição Final. Portanto, o cruzamento de [3, 5) e [2, 7] é [3, 5) e o cruzamento de [3, 5) e [5, 7] é [5, 5] (Observe que [5, 5) é um período vazio.)

Dois vãos se sobrepõem se tiverem posições em comum, exceto na posição Final. Um vão vazio nunca se sobrepõe a qualquer outro período, e a sobreposição de dois vãos nunca é vazia.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> é uma lista de intervalos na ordem das propriedades Iniciar dos períodos. Na lista, são mesclados períodos de sobreposição ou abutting. Por exemplo, dado o conjunto de vãos [5..9] [0.1] [3..6] e [9.10], a lista normalizada de vãos é [0..1] [3..10].

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion e notificações de alteração de texto

O conteúdo de um buffer de <xref:Microsoft.VisualStudio.Text.ITextEdit> texto pode ser alterado usando um objeto. A criação desse objeto (usando `CreateEdit()` um <xref:Microsoft.VisualStudio.Text.ITextBuffer>dos métodos de ) inicia uma transação de texto que consiste em edições de texto. Cada edição é uma substituição de algum período de texto no buffer por uma seqüência. As coordenadas e o conteúdo de cada edição são expressos em relação ao instantâneo do buffer quando a transação foi iniciada. O <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto ajusta as coordenadas das edições que são afetadas por outras edições na mesma transação.

Por exemplo, considere um buffer de texto que contenha essa seqüência:

```
abcdefghij
```

Aplique uma transação que contenha duas edições, uma edição que substitua o `X` vão em [2..4] usando o caractere e `Y`uma segunda edição que substitua o intervalo em [6..9] usando o caractere . O resultado é este buffer:

```
abXefYj
```

As coordenadas para a segunda edição foram calculadas em relação ao conteúdo do buffer no início da transação, antes da primeira edição ser aplicada.

As alterações no buffer <xref:Microsoft.VisualStudio.Text.ITextEdit> surtem efeito quando `Apply()` o objeto é cometido chamando seu método. Se houvesse pelo menos uma edição não <xref:Microsoft.VisualStudio.Text.ITextVersion> vazia, uma <xref:Microsoft.VisualStudio.Text.ITextSnapshot> nova é criada, `Changed` uma nova é criada e um evento é levantado. Cada versão de texto tem um instantâneo de texto diferente. Um instantâneo de texto representa o estado completo do buffer de texto após uma transação de edição, mas uma versão de texto descreve apenas as alterações de um instantâneo para o outro. Em geral, os instantâneos de texto devem ser usados uma vez e depois descartados, enquanto as versões de texto devem permanecer vivas por algum tempo.

Uma versão de <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>texto contém um . Esta coleção descreve as alterações que, quando aplicadas ao snapshot, produzem o snapshot subseqüente. Cada <xref:Microsoft.VisualStudio.Text.ITextChange> uma na coleção contém a posição de caractere da alteração, a seqüência substituída e a seqüência de substituição. A seqüência substituída está vazia para uma inserção básica, e a seqüência de substituição está vazia para uma exclusão básica. A coleção normalizada `null` é sempre para a versão mais recente do buffer de texto.

Apenas <xref:Microsoft.VisualStudio.Text.ITextEdit> um objeto pode ser instanciado para um buffer de texto a qualquer momento, e todas as edições de texto devem ser executadas no segmento que possui o buffer de texto (se a propriedade tiver sido reivindicada). Uma edição de texto pode `Cancel` ser abandonada `Dispose` chamando seu método ou seu método.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>também `Insert()`fornece `Delete()`, `Replace()` e métodos que <xref:Microsoft.VisualStudio.Text.ITextEdit> se assemelham aos encontrados na interface. Chamá-los tem o mesmo <xref:Microsoft.VisualStudio.Text.ITextEdit> efeito que criar um objeto, fazer a chamada semelhante e, em seguida, aplicar a edição.

#### <a name="tracking-points-and-tracking-spans"></a>Pontos de rastreamento e extensões de rastreamento

Um <xref:Microsoft.VisualStudio.Text.ITrackingPoint> representa uma posição de caractere em um buffer de texto. Se o buffer for editado de uma forma que faça com que a posição do personagem mude, o ponto de rastreamento muda com ele. Por exemplo, se um ponto de rastreamento se refere à posição 10 em um buffer e cinco caracteres são inseridos no início do buffer, o ponto de rastreamento refere-se à posição 15. Se uma inserção acontece precisamente na posição denotada pelo <xref:Microsoft.VisualStudio.Text.PointTrackingMode>ponto de rastreamento, seu comportamento é determinado pelo seu , que pode ser ou `Positive` `Negative`. Se o modo de rastreamento for positivo, o ponto de rastreamento refere-se ao mesmo caractere, que agora está no final da inserção. Se o modo de rastreamento for negativo, o ponto de rastreamento refere-se ao primeiro caractere inserido na posição original. Se o caractere na posição representada por um ponto de rastreamento for excluído, o ponto de rastreamento será deslocada para o primeiro caractere que segue o intervalo excluído. Por exemplo, se um ponto de rastreamento se refere ao caractere na posição 5 e os caracteres nas posições 3 a 6 são excluídos, o ponto de rastreamento refere-se ao caractere na posição 3.

Um <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representa uma gama de caracteres em vez de apenas uma posição. Seu comportamento é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>determinado pelo seu . Se o modo de rastreamento de extensão for [SpanTrackingMode.EdgeInclusive,](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)a extensão de rastreamento crescerá para incorporar texto inserido em suas bordas. Se o modo de rastreamento de extensão for [SpanTrackingMode.EdgeExclusive,](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)o período de rastreamento não incorporará texto inserido em suas bordas. No entanto, se o modo de rastreamento de extensão for [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), uma inserção empurra a posição atual para o início e se o modo de rastreamento de span for [SpanTrackingMode.EdgeNegative,](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)uma inserção empurra a posição atual para o final.

Você pode obter a posição de um ponto de rastreamento ou o período de rastreamento de um período de rastreamento para qualquer instantâneo do buffer de texto ao qual eles pertencem. Os pontos de rastreamento e os intervalos de rastreamento podem ser referenciados com segurança a partir de qualquer segmento.

#### <a name="content-types"></a>Tipos de conteúdo

Os tipos de conteúdo são um mecanismo para definir diferentes tipos de conteúdo. Um tipo de conteúdo pode ser um tipo de arquivo como "texto", "código" ou "binário", ou um tipo de tecnologia como "xml", "vb" ou "c#". Por exemplo, a palavra "usar" é uma palavra-chave tanto em C# quanto no Visual Basic, mas não em outras linguagens de programação. Portanto, a definição desta palavra-chave seria limitada aos tipos de conteúdo "c#" e "vb".

Os tipos de conteúdo são usados como filtro para adornos e outros elementos do editor. Muitos recursos do editor e pontos de extensão são definidos por tipo de conteúdo. Por exemplo, a coloração de texto é diferente para arquivos de texto simples, arquivos XML e arquivos de código fonte Visual Basic. Buffers de texto geralmente são atribuídos a um tipo de conteúdo quando são criados, e o tipo de conteúdo de um buffer de texto pode ser alterado.

Os tipos de conteúdo podem herdar múltiplos de outros tipos de conteúdo. O <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> permite especificar vários tipos de base como os pais de um determinado tipo de conteúdo.

Os desenvolvedores podem definir seus próprios <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>tipos de conteúdo e registrá-los usando o . Muitos recursos do editor podem ser definidos em <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>relação a um tipo de conteúdo específico usando o . Por exemplo, margens de editor, adornos e manipuladores de mouse podem ser definidos para que eles se apliquem apenas a editores que exibem determinados tipos de conteúdo.

### <a name="the-text-view"></a>A visualização do texto

A parte de exibição do padrão MVC (Model View Controller) define a exibição do texto, a formatação da exibição, elementos gráficos como a barra de rolagem e o caret. Todos os elementos de apresentação do editor do Visual Studio são baseados no WPF.

#### <a name="text-views"></a>Visualizações de texto

A <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interface é uma representação independente da plataforma de uma exibição de texto. Ele é usado principalmente para exibir documentos de texto em uma janela, mas também pode ser usado para outros fins, por exemplo, em uma dica de ferramenta.

A exibição do texto faz referência a diferentes tipos de buffers de texto. A <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propriedade refere-se a um <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objeto que aponta para esses três buffers de texto diferentes: o buffer de dados, que é o buffer de nível de dados superior, o buffer de edição, no qual ocorre a edição, e o buffer visual, que é o buffer exibido na exibição de texto.

O texto é formatado com base nos classificadores que são anexados ao buffer de texto subjacente, e é adornado usando os provedores de adorno que são anexados à própria exibição de texto.

#### <a name="the-text-view-coordinate-system"></a>O sistema de coordenadas de visualização de texto

O sistema de coordenadas de exibição de texto especifica posições na exibição do texto. Neste sistema de coordenadas, o valor x 0.0 corresponde à borda esquerda do texto que está sendo exibido, e o valor y 0.0 corresponde à borda superior do texto que está sendo exibido. A coordenada x aumenta da esquerda para a direita, e a coordenada y aumenta de cima para baixo.

Uma porta de visualização (a parte do texto visível na janela de texto) não pode ser rolada da mesma maneira horizontalmente que é rolada verticalmente. Uma porta de visualização é rolada horizontalmente alterando sua coordenada esquerda para que se mova em relação à superfície de desenho. No entanto, uma porta de visualização só pode ser rolada verticalmente alterando o texto renderizado, o que faz com que um <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento seja levantado.

As distâncias no sistema de coordenadas correspondem a pixels lógicos. Se a superfície de renderização de texto for exibida sem uma transformação de escala, então uma unidade no sistema de coordenadas de renderização de texto corresponde a um pixel no display.

#### <a name="margins"></a>Margens

A <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interface representa uma margem e permite o controle da visibilidade da margem e seu tamanho. Existem quatro margens predefinidas, que são chamadas de "Topo", "Esquerda", "Direita" e "Inferior" e estão presas à borda superior, inferior, esquerda ou direita de uma vista. Estas margens são contêineres nos quais outras margens podem ser colocadas. A interface define métodos que retornam o tamanho da margem e a visibilidade de uma margem. As margens são elementos visuais que fornecem informações adicionais sobre a exibição de texto à qual estão anexadas. Por exemplo, a margem de número de linha exibe números de linha para a exibição de texto. A margem do glifo exibe elementos de UI.

A <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface lida com a criação e colocação de margens. As margens podem ser ordenadas em relação a outras margens. As margens de maior prioridade estão localizadas mais próximas da exibição do texto. Por exemplo, se houver duas margens esquerdas, margem A e margem B, e a margem B tiver uma prioridade menor que a margem A, a margem B aparecerá à esquerda da margem A.

#### <a name="the-text-view-host"></a>O host de exibição de texto

A <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interface contém a visualização de texto e quaisquer decorações que acompanham a vista, por exemplo, barras de rolagem. O host de exibição de texto também contém margens que estão anexadas a uma borda da exibição.

#### <a name="formatted-text"></a>Texto formatado

O texto exibido em uma exibição <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> de texto é composto por objetos. Cada linha de exibição de texto corresponde a uma linha de texto na exibição do texto. Longas linhas no buffer de texto subjacente podem ser parcialmente obscurecidas (se o embrulho de palavras não estiver ativado) ou divididas em várias linhas de exibição de texto. A <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interface contém métodos e propriedades para mapeamento entre coordenadas e caracteres, e para os adornos que podem estar associados à linha.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>objetos são criados <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> usando uma interface. Se você está apenas preocupado com o texto que é exibido atualmente na exibição, você pode ignorar a fonte de formatação. Se você estiver interessado no formato de texto que não é exibido na exibição (por exemplo, <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> para suportar um corte e colar de texto rico), você pode usar para formatar texto em um buffer de texto.

A exibição de <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> texto formata um de cada vez.

## <a name="editor-features"></a>Recursos do editor

Os recursos do editor são projetados para que a definição do recurso seja separada de sua implementação. O editor inclui esses recursos:

- Tags e classificadores

- Adornos

- Projeção

- Estrutura de tópicos

- Ligações de mouse e chave

- Operações e primitivos

- IntelliSense

### <a name="tags-and-classifiers"></a>Tags e classificadores

Tags são marcadores que estão associados a um período de texto. Eles podem ser apresentados de diferentes maneiras, por exemplo, usando coloração de texto, sublinhados, gráficos ou pop-ups. Classificadores são um tipo de etiqueta.

Outros tipos de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> tags são <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> para destaque de <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> texto, para delineamento e para compilar erros.

#### <a name="classification-types"></a>Tipos de classificação

Uma <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interface representa uma classe de equivalência, que é uma categoria abstrata de texto. Os tipos de classificação podem herdar múltiplos de outros tipos de classificação. Por exemplo, as classificações de linguagem de programação podem incluir "palavra-chave", "comentário" e "identificador", que todos herdam de "código". Os tipos de classificação de linguagem natural podem incluir "substantivo", "verbo" e "adjetivo", que todos herdam da "linguagem natural".

#### <a name="classifications"></a>Classificações

Uma classificação é uma instância de um determinado tipo de classificação, tipicamente em um período de texto. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> é usado para representar uma classificação. Um período de classificação pode ser pensado como um rótulo que cobre um período específico de texto e diz ao sistema que este período de texto é de um tipo de classificação particular.

#### <a name="classifiers"></a>Classificadores

Um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> é um mecanismo que quebra o texto em um conjunto de classificações. Os classificadores devem ser definidos para tipos de conteúdo específicos e instanciados para buffers de texto específicos. Os clientes devem implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para participar da classificação de texto.

#### <a name="classifier-aggregators"></a>Agregadores de classificadores

Um agregador de classificadores é um mecanismo que combina todos os classificadores para um buffer de texto em apenas um conjunto de classificações. Por exemplo, tanto um classificador C# quanto um classificador de língua inglesa poderiam criar classificações sobre um comentário em um arquivo C#. Considere este comentário:

```
// This method produces a classifier
```

Um classificador C# pode rotular todo o período como um comentário, e o classificador de língua inglesa pode classificar "produz" como um "verbo" e "método" como um "substanno". O agregador produz um conjunto de classificações não sobrepostas, e o tipo do conjunto é baseado em todas as contribuições.

Um agregador de classificadores também é um classificador porque divide o texto em um conjunto de classificações. O agregador de classificação também garante que não há classificações sobrepostas e que as classificações são classificadas. Classificadores individuais são livres para retornar qualquer conjunto de classificações, em qualquer ordem, e sobrepostos de qualquer forma.

#### <a name="classification-formatting-and-text-coloring"></a>Formatação de classificação e coloração de texto

A formatação de texto é um exemplo de um recurso que é construído na classificação de texto. Ele é usado pela camada de exibição de texto para determinar a exibição do texto em um aplicativo. A área de formatação de texto depende do WPF, mas a definição lógica de classificações não.

Um formato de classificação é um conjunto de propriedades de formatação para um tipo de classificação específica. Esses formatos herdam do formato do pai do tipo de classificação.

Um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> é um mapa de um tipo de classificação para um conjunto de propriedades de formatação de texto. A implementação do mapa de formato no editor trata de todas as exportações de formatos de classificação.

### <a name="adornments"></a>Adornos

Adornos são efeitos gráficos que não estão diretamente relacionados com a fonte e a cor dos caracteres na exibição de texto. Por exemplo, o sublinhado vermelho squiggle que é usado para marcar código não-compilação em muitas linguagens de programação é um adorno incorporado, e dicas de ferramentas são adornos pop-up. Os adornos são <xref:System.Windows.UIElement> derivados <xref:Microsoft.VisualStudio.Text.Tagging.ITag>e implementam. Dois tipos especializados de etiqueta <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>de adorno são os adornos que ocupam o <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>mesmo espaço que o texto em uma vista, e o , para o sublinhado squiggle.

Adornos incorporados são gráficos que fazem parte da exibição de texto formatado. Eles são organizados em diferentes camadas de ordem Z. Há três camadas incorporadas, como segue: texto, cuidado e seleção. No entanto, os desenvolvedores podem definir mais camadas e colocá-las em ordem em relação umas às outras. Os três tipos de adornos incorporados são adornos relativos ao texto (que se movem quando o texto se move e são excluídos quando o texto é excluído), adornos relativos à exibição (que têm a ver com partes não-texto da exibição) e adornos controlados pelo proprietário (o desenvolvedor deve gerenciar sua colocação).

Adornos pop-up são gráficos que aparecem em uma pequena janela acima da exibição de texto, por exemplo, dicas de ferramentas.

### <a name="projection"></a><a name="projection"></a>Projeção

Projeção é uma técnica para construir um tipo diferente de buffer de texto que não armazena texto, mas combina texto de outros buffers de texto. Por exemplo, um buffer de projeção pode ser usado para concatecar o texto de dois outros buffers e apresentar o resultado como se estivesse em apenas um buffer, ou para ocultar partes do texto em um buffer. Um buffer de projeção pode atuar como um buffer de origem para outro buffer de projeção. Um conjunto de buffers que são relacionados por projeção pode ser construído para reorganizar o texto de muitas maneiras diferentes. (Esse conjunto também é conhecido como gráfico *tampão*.) O recurso de delineamento de texto do Visual Studio é implementado usando um buffer de projeção para ocultar o texto colapsado, e o editor do Visual Studio para páginas ASP.NET usa projeção para suportar linguagens incorporadas, como Visual Basic e C#.

Um <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> é criado <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>usando . Um buffer de projeção é <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representado por uma seqüência ordenada de objetos que são conhecidos como *intervalos de origem*. O conteúdo desses intervalos é apresentado como uma seqüência de caracteres. Os buffers de texto dos quais os intervalos de origem são desenhados são chamados *buffers de origem*. Os clientes de um buffer de projeção não precisam estar cientes de que ele difere de um buffer de texto comum.

O buffer de projeção ouve eventos de alteração de texto nos buffers de origem. Quando o texto em uma extensão de origem muda, o buffer de projeção mapeia as coordenadas de texto alteradas para suas próprias coordenadas e levanta eventos apropriados de mudança de texto. Por exemplo, considere os buffers de origem A e B que tenham esses conteúdos:

```
A: ABCDE
B: vwxyz
```

Se o buffer de projeção P for formado a partir de dois períodos de texto, um que tenha todo o buffer A e o outro que tenha todo o buffer B, então P tem o seguinte conteúdo:

```
P: ABCDEvwxyz
```

Se a `xy` substring for excluída do buffer B, o buffer P levanta um evento que indica que os caracteres das posições 7 e 8 foram excluídos.

O buffer de projeção também pode ser editado diretamente. Ele propaga edições para os buffers de origem apropriados. Por exemplo, se uma seqüência for inserida no buffer P na posição 6 (a posição original do caractere "v"), a inserção será propagada para buffer B na posição 1.

Há restrições nas extensões de origem que contribuem para um buffer de projeção. Os intervalos de origem podem não se sobrepor; um local em um buffer de projeção não pode mapear para mais de um local em qualquer buffer de origem, e um local em um buffer de origem não pode mapear para mais de um local em um buffer de projeção. Não são permitidas circularidades na relação de buffer de origem.

Os eventos são levantados quando o conjunto de buffers de origem para um buffer de projeção muda e quando o conjunto de intervalos de origem muda.
Um tampão de elision é um tipo especial de tampão de projeção. É usado principalmente para delineamento e para operações que expandem e colapsam blocos de texto. Um buffer de elision é baseado em apenas um buffer de origem, e os intervalos no buffer de elision devem ser ordenados da mesma forma que são ordenados no buffer de origem.

#### <a name="the-buffer-graph"></a>O gráfico tampão

A <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interface permite o mapeamento através de um gráfico de buffers de projeção. Todos os buffers de texto e buffers de projeção são coletados em um gráfico acíclico direcionado, assim como a árvore de sintaxe abstrata que é produzida por um compilador de linguagem. O gráfico é definido pelo buffer superior, que pode ser qualquer buffer de texto. O gráfico tampão pode mapear de um ponto no buffer superior até um ponto em um buffer de origem, ou de um intervalo no buffer superior para um conjunto de intervalos em um buffer de origem. Da mesma forma, ele pode mapear um ponto ou se estender de um buffer de origem a um ponto no buffer superior. Os gráficos tampão são <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>criados usando o .

#### <a name="events-and-projection-buffers"></a>Tampões de eventos e projeções

Quando um buffer de projeção é modificado, as modificações são enviadas do buffer de projeção para os buffers que dependem dele. Depois que todos os buffers são modificados, eventos de alteração de buffer são levantados, começando com o buffer mais profundo.

### <a name="outlining"></a>Estrutura de tópicos

Delineamento é a capacidade de expandir ou colapsar diferentes blocos de texto em uma exibição de texto. O delineamento é <xref:Microsoft.VisualStudio.Text.Tagging.ITag>definido como uma espécie de , da mesma forma que os adornos são definidos. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> é uma tag que define uma região de texto que pode ser expandida ou colapsada. Para usar o delineamento, você deve importar o <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> para obter um <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. O gerente delineamento enumera, colapsa e expande os <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> diferentes blocos, que são representados como objetos, e levanta os eventos em conformidade.

### <a name="mouse-bindings"></a>Amarras do mouse

As vinculações do mouse vinculam os movimentos do mouse a diferentes comandos. As ligações do mouse <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>são definidas usando um , <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>e as amarras de chave são definidas usando um . O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> instantaneamente instancia todas as ligações e as conecta a eventos do mouse na exibição.

A <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interface contém manipuladores de eventos pré-processo e pós-processo para diferentes eventos do mouse. Para lidar com um dos eventos, você pode <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>substituir alguns dos métodos em .

### <a name="editor-operations"></a>Operações do editor

As operações do editor podem ser usadas para automatizar a interação com o editor, para scripts ou outros propósitos. Você pode <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> importar as operações <xref:Microsoft.VisualStudio.Text.Editor.ITextView>de acesso a um dado . Em seguida, você pode usar esses objetos para modificar a seleção, rolar a exibição ou mover o cuidado para diferentes partes da exibição.

### <a name="intellisense"></a>IntelliSense

O IntelliSense suporta a conclusão de declarações, ajuda de assinatura (também conhecida como informações de parâmetro), Informações Rápidas e lâmpadas.

A conclusão da declaração fornece listas pop-up de possíveis conclusões para nomes de métodos, elementos XML e outros elementos de codificação ou marcação. Em geral, um gesto de usuário invoca uma sessão de conclusão. A sessão exibe a lista de possíveis conclusões e o usuário pode selecionar uma ou descartar a lista. O <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> é responsável por criar <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>e acionar o . O <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> cálculo <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> dos itens de conclusão para a sessão.

## <a name="see-also"></a>Confira também

- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
- [Importações do editor](../extensibility/editor-imports.md)
