---
title: Pontos de extensão do Serviço de Idiomas e Editores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703051"
---
# <a name="language-service-and-editor-extension-points"></a>Pontos de extensão de serviços de idiomas e editores
O editor fornece pontos de extensão que você pode estender como partes componentes do Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada), incluindo a maioria dos recursos de serviço de idioma. Estas são as principais categorias de pontos de extensão:

- Tipos de conteúdo

- Tipos de classificação e formatos de classificação

- Margens e roltas

- Marcas

- Adornos

- Processadores de mouse

- Manipuladores de queda

- Opções

- IntelliSense

## <a name="extend-content-types"></a>Estender tipos de conteúdo
 Os tipos de conteúdo são as definições dos tipos de texto manuseados pelo editor, por exemplo, "texto", "código" ou "CSharp". Você define um novo tipo de conteúdo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> declarando uma variável do tipo e dando ao novo tipo de conteúdo um nome único. Para registrar o tipo de conteúdo com o editor, exporte-o juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>é o nome do tipo de conteúdo.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>é o nome do tipo de conteúdo do qual este tipo de conteúdo é derivado. Um tipo de conteúdo pode herdar de vários outros tipos de conteúdo.

  Como <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> a classe está selada, você pode exportá-la sem parâmetro de tipo.

  O exemplo a seguir mostra atributos de exportação em uma definição de tipo de conteúdo.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Os tipos de conteúdo podem ser baseados em zero ou mais tipos de conteúdo pré-existentes. Estes são os tipos incorporados:

- Qualquer: o tipo de conteúdo básico. Pai de todos os outros tipos de conteúdo.

- Texto: o tipo básico para conteúdo não-projeção. Herda de "qualquer".

- Texto simples: para texto sem código. Herda do "texto".

- Código: para código de todos os tipos. Herda do "texto".

- Inerte: exclui o texto de qualquer tipo de manuseio. O texto deste tipo de conteúdo nunca terá qualquer extensão aplicada a ele.

- Projeção: para o conteúdo de buffers de projeção. Herda de "qualquer".

- Intellisense: para o conteúdo do IntelliSense. Herda do "texto".

- Sighelp: ajuda de assinatura. Herda do "intellisense".

- Sighelp-doc: documentação de ajuda de assinatura. Herda do "intellisense".

  Estes são alguns dos tipos de conteúdo que são definidos pelo Visual Studio e alguns dos idiomas hospedados no Visual Studio:

- Basic

- C/C++

- Saída do console

- CSharp

- CSS

- Enc

- Encontrar resultados

- F#

- HTML

- JScript

- XAML

- XML

  Para descobrir a lista de tipos <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>de conteúdo disponíveis, importe o , que mantém a coleção de tipos de conteúdo para o editor. O código a seguir importa este serviço como propriedade.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Para associar um tipo de conteúdo <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>a uma extensão de nome de arquivo, use .

> [!NOTE]
> No Visual Studio, as extensões de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> nome de arquivo são registradas usando o pacote de serviço em um idioma. Os <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associados são um tipo de conteúdo MEF com uma extensão de nome de arquivo que tenha sido registrada desta forma.

 Para exportar a extensão do nome do arquivo para a definição de tipo de conteúdo, você deve incluir os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: especifica a extensão do nome do arquivo.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: especifica o tipo de conteúdo.

  Como <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> a classe está selada, você pode exportá-la sem parâmetro de tipo.

  O exemplo a seguir mostra atributos de exportação em uma extensão de nome de arquivo para uma definição de tipo de conteúdo.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 O <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gerencia as associações entre extensões de nome de arquivo e tipos de conteúdo.

## <a name="extend-classification-types-and-classification-formats"></a>Estender os tipos de classificação e os formatos de classificação
 Você pode usar tipos de classificação para definir os tipos de texto para os quais deseja fornecer um manuseio diferente (por exemplo, colorindo o texto "keyword" azul e o "comentário" verde texto). Defina um novo tipo de classificação declarando uma variável de tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> e dando-lhe um nome único.

 Para registrar o tipo de classificação com o editor, exporte-o juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do tipo de classificação.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: o nome do tipo de classificação a partir do qual este tipo de classificação herda. Todos os tipos de classificação herdam de "texto", e um tipo de classificação pode herdar de vários outros tipos de classificação.

  Como <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> a classe está selada, você pode exportá-la sem parâmetro de tipo.

  O exemplo a seguir mostra atributos de exportação em uma definição de tipo de classificação.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 O <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fornece acesso a classificações padrão. Os tipos de classificação incorporados incluem:

- "texto"

- "linguagem natural" (deriva de "texto")

- "linguagem formal" (deriva de "texto")

- "string" (deriva de "literal")

- "personagem" (deriva de "literal")

- "numérico" (deriva de "literal")

  Um conjunto de diferentes <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>tipos de erro herdados de . Eles incluem os seguintes tipos de erro:

- "Erro de sintaxe"

- "erro do compilador"

- "outro erro"

- "Aviso"

  Para descobrir a lista de tipos <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>de classificação disponíveis, importe o , que mantém a coleção de tipos de classificação para o editor. O código a seguir importa este serviço como propriedade.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Você pode definir uma definição de formato de classificação para o seu novo tipo de classificação. Obtenha uma <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> classe e exporte-a com o tipo, <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do formato.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: o nome de exibição do formato.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: especifica se o formato aparece na página **Fontes e Cores** da caixa de diálogo **Opções.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a prioridade do formato. Os valores <xref:Microsoft.VisualStudio.Text.Classification.Priority>válidos são de .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: o nome do tipo de classificação para o qual este formato é mapeado.

  O exemplo a seguir mostra atributos de exportação em uma definição de formato de classificação.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Para descobrir a lista de formatos disponíveis, importe o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, que mantém a coleção de formatos para o editor. O código a seguir importa este serviço como propriedade.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Estender margens e roltas
 Margens e rolagem são os principais elementos de exibição do editor, além da própria visualização de texto. Você pode fornecer qualquer número de margens, além das margens padrão que aparecem em torno da exibição de texto.

 Implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> uma interface para definir uma margem. Você também deve <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> implementar a interface para criar a margem.

 Para registrar o provedor de margem com o editor, você deve exportar o provedor juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome da margem.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem em que a margem aparece, em relação às outras margens.

   Estas são as margens incorporadas:

  - "Barra de Rolagem Horizontal Wpf"

  - "Barra de Rolagem Vertical Wpf"

  - "Margem numérica da linha WPF"

    As margens horizontais `After="Wpf Horizontal Scrollbar"` que possuem um atributo de ordem são exibidas abaixo `Before ="Wpf Horizontal Scrollbar"` da margem incorporada, e as margens horizontais que têm um atributo de ordem são exibidas acima da margem incorporada. As margens verticais `After="Wpf Vertical Scrollbar"` direitas que têm um atributo de ordem são exibidas à direita da barra de rolagem. Margens verticais esquerdas que têm um atributo de ordem de `After="Wpf Line Number Margin"` aparecer à esquerda da margem numérica da linha (se for visível).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: o tipo de margem (esquerda, direita, superior ou inferior).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "texto" ou "código") para o qual sua margem é válida.

  O exemplo a seguir mostra atributos de exportação em um provedor de margem para uma margem que aparece à direita da margem numérica de linha.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Estender tags
 Tags são uma maneira de associar dados com diferentes tipos de texto. Em muitos casos, os dados associados são exibidos como um efeito visual, mas nem todas as tags têm uma apresentação visual. Você pode definir seu próprio tipo <xref:Microsoft.VisualStudio.Text.Tagging.ITag>de tag implementando . Você também <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> deve implementar para fornecer as tags para um <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> determinado conjunto de períodos de texto e um para fornecer o tagger. Você deve exportar o provedor de tagger juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "texto" ou "código") para o qual sua tag é válida.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: o tipo de tag.

  O exemplo a seguir mostra atributos de exportação em um provedor de tagger.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 Os seguintes tipos de tag estão incorporados:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associado <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>a um .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associado aos tipos de erro.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associado a um adorno.

  > [!NOTE]
  > Para um exemplo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>de : consulte a definição HighlightWordTag em [Passo a Passo: Texto de destaque](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associada sísticas que podem ser expandidas ou colapsadas em delineamento.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: define o espaço que um adorno ocupa em uma exibição de texto. Para obter mais informações sobre adornos de negociação espacial, consulte a seção a seguir.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornece espaçamento automático e dimensionamento para o adorno.

  Para encontrar e usar tags para buffers <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>e visualizações, <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> importe o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> ou o , que lhe dão um do tipo solicitado. O código a seguir importa este serviço como propriedade.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tags e MarkerFormatDefinições
 Você pode <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> estender a classe para definir a aparência de uma tag. Você deve exportar sua <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>classe (como a) com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome usado para referenciar este formato

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: isso faz com que o formato apareça na ui

  Na construtora, você define o nome de exibição e a aparência da tag. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>define a cor de <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> preenchimento e define a cor da borda. O <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> é o nome localizado da definição de formato.

  A seguir, um exemplo de definição de formato:

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 Para aplicar essa definição de formato a uma tag, faça referência ao nome definido no atributo nome da classe (não o nome de exibição).

> [!NOTE]
> Para um exemplo <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>de : consulte a classe HighlightWordFormatDefinition no [Passo a Passo: Destacando texto](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Estender adornos
 Adornos definem efeitos visuais que podem ser adicionados tanto ao texto exibido em uma exibição de texto quanto à própria exibição de texto. Você pode definir seu próprio adorno como qualquer tipo de <xref:System.Windows.UIElement>.

 Em sua aula de adorno, você deve declarar um <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Para registrar sua camada de adorno, exporte-a juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do adorno.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordenação do adorno em relação a outras camadas de adorno. A <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> classe define quatro camadas padrão: Seleção, Delineamento, Caret e Texto.

  O exemplo a seguir mostra atributos de exportação em uma definição de camada de adorno.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Você deve criar uma segunda <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> classe que <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> implemente e manuseie seu evento instanciando o adorno. Você deve exportar esta classe juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "texto" ou "código") para o qual o adorno é válido.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: o tipo de visualização de texto para a qual este adorno é válido. A <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> classe tem o conjunto de funções de exibição de texto predefinidas. Por exemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> é usado principalmente para visualizações de texto de arquivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>é usado para visualizações de texto que um usuário pode editar ou navegar usando um mouse e teclado. Exemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> visualizações são a exibição de texto do editor e a janela **Saída.**

  O exemplo a seguir mostra atributos de exportação no provedor de adornos.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Um adorno de negociação espacial é aquele que ocupa espaço no mesmo nível do texto. Para criar esse tipo de adorno, você deve <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>definir uma classe de tag que herda, que define a quantidade de espaço que o adorno ocupa.

 Como em todos os adornos, você deve exportar a definição de camada de adorno.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Para instanciar o adorno de negociação espacial, <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>você deve criar uma <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> classe que implemente, além da classe que implementa (como acontece com outros tipos de adornos).

 Para registrar o provedor de tagger, você deve exportá-lo juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "texto" ou "código") para o qual seu adorno é válido.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: o tipo de exibição de texto para a qual esta tag ou adorno é válido. A <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> classe tem o conjunto de funções de exibição de texto predefinidas. Por exemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> é usado principalmente para visualizações de texto de arquivos. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>é usado para visualizações de texto que um usuário pode editar ou navegar usando um mouse e teclado. Exemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> visualizações são a exibição de texto do editor e a janela **Saída.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: o tipo de tag ou adorno que você definiu. Você deve adicionar <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>um segundo para .

  O exemplo a seguir mostra atributos de exportação no provedor de tagger para uma tag de adornmento de negociação espacial.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Estendendo processadores de mouse
 Você pode adicionar manuseio especial para entrada do mouse. Crie uma classe que <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> herde e anule os eventos do mouse para a entrada que você deseja lidar. Você também <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> deve implementar em uma segunda <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> classe e exportá-lo juntamente com o que especifica o tipo de conteúdo (por exemplo, "texto" ou "código") para o qual o manipulador do mouse é válido.

 O exemplo a seguir mostra atributos de exportação em um provedor de processador de mouse.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Estender manipuladores de queda
 Você pode personalizar o comportamento dos manipuladores de gota para <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> tipos específicos de <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> texto, criando uma classe que implementa e uma segunda classe que implementa para criar o manipulador de queda. Você deve exportar o manipulador de gotas juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: o formato de texto para o qual este manipulador de gotas é válido. Os seguintes formatos são tratados em ordem prioritária do mais alto para o mais baixo:

  1. Qualquer formato personalizado

  2. Filedrop

  3. Arquivo EnhancedMeta

  4. Waveaudio

  5. Riff

  6. Dif

  7. Local

  8. Paleta

  9. PenData

  10. Serializável

  11. Link Simbólico

  12. Xaml

  13. Xamlpackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Formato HTML

  21. Unicodetext

  22. OEMText

  23. Texto

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do manipulador de gotas.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem do manipulador de queda antes ou depois do manipulador de queda padrão. O manipulador de queda padrão do Visual Studio é chamado "DefaultFileDropHandler".

  O exemplo a seguir mostra atributos de exportação em um provedor de manipulador de gotas.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Ampliando as opções do editor
 Você pode definir opções para serem válidas apenas em um determinado escopo, por exemplo, em uma exibição de texto. O editor fornece este conjunto de opções predefinidas: opções de editor, opções de exibição e opções de exibição do Windows Presentation Foundation (WPF). Essas opções podem <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>ser <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>encontradas em , e .

 Para adicionar uma nova opção, obtenha uma classe de uma dessas classes de definição de opção:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  O exemplo a seguir mostra como exportar uma definição de opção que tenha um valor booleano.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Estender o IntelliSense
 IntelliSense é um termo geral para um grupo de recursos que fornecem informações sobre texto estruturado e conclusão de declarações para ele. Esses recursos incluem conclusão de declaração, ajuda de assinatura, Informações Rápidas e lâmpadas. A conclusão da declaração ajuda os usuários a digitar uma palavra-chave do idioma ou o nome do membro corretamente. A ajuda de assinatura exibe a assinatura ou assinaturas para o método que o usuário acabou de digitar. O Quick Info exibe uma assinatura completa para um tipo ou nome de membro quando o mouse repousa sobre ele. A lâmpada fornece ações adicionais para certos identificadores em determinados contextos, por exemplo, renomeando todas as ocorrências de uma variável após uma ocorrência ter sido renomeada.

 O design de um recurso IntelliSense é praticamente o mesmo em todos os casos:

- Um *corretor* da IntelliSense é responsável pelo processo geral.

- Uma *sessão* intelliSense representa a seqüência de eventos entre o acionamento do apresentador e o confirmação ou cancelamento da seleção. A sessão é normalmente desencadeada por algum gesto do usuário.

- Um *controlador* IntelliSense é responsável por decidir quando a sessão deve começar e terminar. Também decide quando as informações devem ser cometidas e quando a sessão deve ser cancelada.

- Uma *fonte* da IntelliSense fornece o conteúdo e decide a melhor combinação.

- Um *apresentador* da IntelliSense é responsável por exibir o conteúdo.

  Na maioria dos casos, recomendamos que você forneça pelo menos uma fonte e um controlador. Você também pode fornecer um apresentador se quiser personalizar o display.

### <a name="implement-an-intellisense-source"></a>Implementar uma fonte IntelliSense
 Para personalizar uma fonte, você deve implementar uma (ou mais) das seguintes interfaces de origem:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>foi preterido em <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>favor de .

 Além disso, você deve implementar um provedor do mesmo tipo:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>foi preterido em <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>favor de .

 Você deve exportar o provedor juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome da fonte.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "texto" ou "código") ao qual a fonte se aplica.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem em que a fonte deve aparecer (em relação a outras fontes).

- O exemplo a seguir mostra atributos de exportação em um provedor de origem de conclusão.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Para obter mais informações sobre a implementação de fontes do IntelliSense, consulte os seguintes passos a passo:

- [Passo a passo: Exibir dicas de ferramentas do QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Passo a passo: Ajuda de assinatura de exibição](../extensibility/walkthrough-displaying-signature-help.md)

- [Passo a passo: exibir preenchimento de declaração](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementar um controlador IntelliSense
 Para personalizar um controlador, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> você deve implementar a interface. Além disso, você deve implementar um provedor controlador juntamente com os seguintes atributos:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do controlador.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "texto" ou "código") ao qual o controlador se aplica.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem em que o controlador deve aparecer (em relação a outros controladores).

  O exemplo a seguir mostra atributos de exportação em um provedor controlador de conclusão.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Para obter mais informações sobre como usar os controladores IntelliSense, consulte os seguintes passos a passo:

- [Passo a passo: Exibir dicas de ferramentas do QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
