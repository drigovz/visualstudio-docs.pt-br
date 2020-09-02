---
title: 'Walkthrough: exibindo marcas inteligentes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: 116f76324a2150413c0ae6d08bc99e114efcc50e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805575"
---
# <a name="walkthrough-displaying-smarttags"></a>Passo a passo: exibindo SmartTags
Marcas inteligentes são preteridas em favor de lâmpadas leves. Consulte [Walkthrough: exibindo sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Marcas inteligentes são marcas no texto que se expandem para exibir um conjunto de ações. Por exemplo, em um projeto do Visual Basic ou do Visual C#, uma linha vermelha aparece em uma palavra quando você renomeia um identificador, como um nome de variável. Quando você move o ponteiro sobre o sublinhado, um botão é exibido próximo ao ponteiro. Se você clicar no botão, uma ação sugerida será exibida, por exemplo, **renomear IsRead como IsReady**. Se você clicar na ação, todas as referências a **IsRead** no projeto serão renomeadas como **IsReady**.  
  
 Embora as marcas inteligentes façam parte da implementação do IntelliSense no editor, você pode implementar marcas inteligentes por meio de subclasses <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> e, em seguida, implementar a <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interface e a <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> interface.  
  
> [!NOTE]
> Outros tipos de marcas podem ser implementados de maneira semelhante.  
  
 A instrução a seguir mostra como criar uma marca inteligente que aparece na palavra atual e tem duas ações sugeridas: **converter em maiúsculas** e **converter em**minúsculas.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto do MEF  
  
1. Crie um projeto classificador de editor. Nomeie a solução `SmartTagTest` .  
  
2. Abra o arquivo Source. Extension. vsixmanifest no editor de manifesto do VSIX.  
  
3. Verifique se a seção **ativos** contém um `Microsoft.VisualStudio.MefComponent` tipo, se a **origem** está definida como e `A project in current solution` se o **projeto** está definido como SmartTagTest.dll.  
  
4. Salve e feche Source. Extension. vsixmanifest.  
  
5. Adicione a seguinte referência ao projeto e defina **CopyLocal** como `false` :  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
6. Exclua os arquivos de classe existentes.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementando um marcador para marcas inteligentes  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Para implementar um marcador para marcas inteligentes  
  
1. Adicione um arquivo de classe e nomeie-o `TestSmartTag` .  
  
2. Adicione as seguintes importações:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Adicione uma classe denominada `TestSmartTag` herdada de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Adicione um construtor para essa classe que chama o construtor base com um <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , o que fará com que uma linha azul apareça no primeiro caractere de uma palavra. (Se você usar <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , uma linha vermelha aparecerá sob o último caractere da palavra.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Adicione uma classe chamada `TestSmartTagger` que herde de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> do tipo `TestSmartTag` e implementa <xref:System.IDisposable> .  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Adicione os campos particulares a seguir à classe de marca.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Adicione um construtor que defina os campos particulares e assine o <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. Implemente para <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> que a marca seja criada para a palavra atual. (Esse método também chama um método privado `GetSmartTagActions` que é explicado posteriormente.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Adicione um `GetSmartTagActions` método para configurar as ações de marca inteligente. As ações em si são implementadas em etapas posteriores.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Declare o `SmartTagsChanged` evento.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implemente o `OnLayoutChanged` manipulador de eventos para gerar o `TagsChanged` evento, que faz com que <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> seja chamado.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implemente o <xref:System.IDisposable.Dispose%2A> método para que ele cancele a assinatura do <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementando o provedor de marcação de marca inteligente  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Para implementar o provedor de marcação de marca inteligente  
  
1. Adicione uma classe denominada `TestSmartTagTaggerProvider` herdada de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Exporte-o com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes de = "padrão" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. Importe o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> como uma propriedade.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Implementar o método de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> .  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementando ações de marca inteligente  
  
#### <a name="to-implement-smart-tag-actions"></a>Para implementar ações de marca inteligente  
  
1. Crie duas classes, o primeiro nome `UpperCaseSmartTagAction` e o segundo nomeado `LowerCaseSmartTagAction` . Ambas as classes implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction> .  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Ambas as classes são semelhantes, exceto que uma chamada <xref:System.String.ToUpper%2A> e as outras chamadas <xref:System.String.ToLower%2A> . As etapas a seguir abrangem apenas a classe de ação de letras maiúsculas, mas você deve implementar ambas as classes. Use as etapas para implementar a ação em maiúsculas como um padrão para implementar a ação em minúsculas.  
  
2. Declare um conjunto de campos privados.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Adicione um construtor que defina os campos.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Implemente as propriedades da seguinte maneira.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Implemente o <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> método substituindo o texto no span por seu equivalente em maiúsculas.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
 Para testar esse código, crie a solução SmartTagTest e execute-a na instância experimental.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Para compilar e testar a solução SmartTagTest  
  
1. Compile a solução.  
  
2. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3. Crie um arquivo de texto e digite algum texto.  
  
     Uma linha azul deve ser exibida na primeira letra da primeira palavra do texto.  
  
4. Mova o ponteiro sobre a linha azul.  
  
     Um botão deve ser exibido próximo ao ponteiro.  
  
5. Quando você clica no botão, duas ações sugeridas devem ser exibidas: **converter em letras maiúsculas** e **converter em letras**minúsculas. Se você clicar na primeira ação, todo o texto na palavra atual deverá ser convertido em letras maiúsculas. Se você clicar na segunda ação, todo o texto deverá ser convertido em letras minúsculas.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)