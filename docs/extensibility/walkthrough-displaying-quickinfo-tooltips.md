---
title: 'Passo a passo: Exibindo dicas de ferramentas do QuickInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697433"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Passo a passo: Exibir dicas de ferramentas do QuickInfo
QuickInfo é um recurso do IntelliSense que exibe assinaturas e descrições do método quando um usuário move o ponteiro sobre um nome de método. Você pode implementar recursos baseados em idioma, como o QuickInfo, definindo os identificadores para os quais deseja fornecer descrições quickInfo e, em seguida, criando uma dica de ferramenta para exibir o conteúdo. Você pode definir o QuickInfo no contexto de um serviço de idioma, ou pode definir sua própria extensão de nome de arquivo e tipo de conteúdo e exibir o QuickInfo para esse tipo, ou pode exibir o QuickInfo para um tipo de conteúdo existente (como "texto"). Este passo a passo mostra como exibir o QuickInfo para o tipo de conteúdo "texto".

 O exemplo quickInfo neste passo a passo exibe as dicas de ferramentas quando um usuário move o ponteiro sobre um nome de método. Este design exige que você implemente essas quatro interfaces:

- interface de origem

- interface provedor de origem

- interface do controlador

- interface do provedor de controlador

  Os provedores de origem e controlador são partes componentes do Mef (Managed Extensibility Framework, estrutura de <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>extensibilidade gerenciada) e <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>são responsáveis por exportar as classes de origem e controladore importar serviços e corretores, como o , que cria o buffer de texto da dica de ferramenta, e o , que aciona a sessão QuickInfo.

  Neste exemplo, a fonte QuickInfo usa uma lista codificada de nomes e descrições de métodos, mas em implementações completas, o serviço de idiomas e a documentação do idioma são responsáveis por fornecer esse conteúdo.

## <a name="prerequisites"></a>Pré-requisitos
 Começando no Visual Studio 2015, você não precisa instalar o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Crie um projeto MEF

### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `QuickInfoTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

## <a name="implement-the-quickinfo-source"></a>Implementar a fonte QuickInfo
 A fonte QuickInfo é responsável por coletar o conjunto de identificadores e suas descrições e adicionar o conteúdo ao buffer de texto da dica de ferramenta quando um dos identificadores é encontrado. Neste exemplo, os identificadores e suas descrições são adicionados apenas no construtor de origem.

#### <a name="to-implement-the-quickinfo-source"></a>Para implementar a fonte QuickInfo

1. Adicione um arquivo de `TestQuickInfoSource`classe e nomeie-o .

2. Adicione uma referência ao *Microsoft.VisualStudio.Language.IntelliSense*.

3. Adicione as seguintes importações.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Declare uma classe <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>que implemente `TestQuickInfoSource`e nomeie-a.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Adicione campos para o provedor de origem QuickInfo, o buffer de texto e um conjunto de nomes de métodos e assinaturas de métodos. Neste exemplo, os nomes e assinaturas do `TestQuickInfoSource` método são inicializados na construtora.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Adicione um construtor que define o provedor de origem QuickInfo e o buffer de texto e preencha o conjunto de nomes de métodos e assinaturas e descrições do método.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> . Neste exemplo, o método encontra a palavra atual ou a palavra anterior se o cursor estiver no final de uma linha ou de um buffer de texto. Se a palavra for um dos nomes do método, a descrição do nome desse método será adicionada ao conteúdo do QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Você também deve implementar um método <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> Descarte() uma vez que implementa: <xref:System.IDisposable>

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementar um provedor de origem QuickInfo
 O provedor da fonte QuickInfo serve principalmente para exportar-se como uma parte componente MEF e instanciar a fonte QuickInfo. Por ser uma peça componente MEF, pode importar outras peças componentes MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar um provedor de origem QuickInfo

1. Declare um provedor de `TestQuickInfoSourceProvider` origem <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>QuickInfo chamado que <xref:Microsoft.VisualStudio.Utilities.NameAttribute> implementa e exporte-o com um de "ToolTip QuickInfo Source", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Antes="default" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importar dois serviços de editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, como propriedades de `TestQuickInfoSourceProvider`.

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para retornar `TestQuickInfoSource`um novo .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementar um controlador QuickInfo
 Os controladores QuickInfo determinam quando o QuickInfo é exibido. Neste exemplo, quickInfo aparece quando o ponteiro é sobre uma palavra que corresponde a um dos nomes do método. O controlador QuickInfo implementa um manipulador de eventos de mouse hover que aciona uma sessão QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Para implementar um controlador QuickInfo

1. Declare uma classe <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>que implemente `TestQuickInfoController`e nomeie-a.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Adicione campos privados para a exibição de texto, os buffers de texto representados na exibição de texto, na sessão QuickInfo e no provedor de controle QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Adicione um construtor que define os campos e adiciona o manipulador de eventos mouse hover.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Adicione o manipulador de eventos do mouse hover que aciona a sessão QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> o método para que ele remova o manipulador de eventos do mouse hover quando o controlador estiver separado da exibição de texto.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> método e o método como métodos vazios para este exemplo.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementando o provedor de controle QuickInfo
 O provedor do controlador QuickInfo serve principalmente para exportar-se como uma parte componente MEF e instanciar o controlador QuickInfo. Por ser uma peça componente MEF, pode importar outras peças componentes MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar o provedor de controle QuickInfo

1. Declare uma `TestQuickInfoControllerProvider` classe nomeada <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>que implementa <xref:Microsoft.VisualStudio.Utilities.NameAttribute> e exporte-a com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "ToolTip QuickInfo Controller" e um de "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importe <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como propriedade.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> o método instanciando o controlador QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Construa e teste o Código
 Para testar esse código, construa a solução QuickInfoTest e execute-o na instância experimental.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para construir e testar a solução QuickInfoTest

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto que inclua as palavras "adicionar" e "subtrair".

4. Mova o ponteiro sobre uma das ocorrências de "add". A assinatura e a `add` descrição do método devem ser exibidas.

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
