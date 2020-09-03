---
title: 'Walkthrough: Personalizando a exibição de texto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202020"
---
# <a name="walkthrough-customizing-the-text-view"></a>Passo a passo: personalizando a exibição de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode personalizar uma exibição de texto modificando qualquer uma das seguintes propriedades em seu mapa de formato de editor:  
  
- Margem de indicadores  
  
- Cursor de inserção  
  
- Substituir cursor  
  
- Texto selecionado  
  
- Texto selecionado inativo (ou seja, o texto selecionado que perdeu o foco)  
  
- Espaço em branco visível  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto do MEF  
  
1. Crie um projeto VSIX em C#. (Na caixa de diálogo **novo projeto** , selecione **Visual C#/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `ViewPropertyTest` .  
  
2. Adicione um modelo de item de classificação do editor ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Exclua os arquivos de classe existentes.  
  
## <a name="defining-the-content-type"></a>Definindo o tipo de conteúdo  
  
1. Adicione um arquivo de classe e nomeie-o `ViewPropertyModifier` .  
  
2. Adicione as seguintes diretivas `using`:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Declare uma classe denominada `TestViewCreationListener` herdada de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exporte esta classe com os seguintes atributos:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar o tipo de conteúdo ao qual este ouvinte se aplica.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar a função deste ouvinte.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. Nessa classe, importe o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Alterando as propriedades da exibição  
  
1. Implemente o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que as propriedades de exibição sejam alteradas quando a exibição for aberta. Para fazer a alteração, primeiro localize o <xref:System.Windows.ResourceDictionary> que corresponde ao aspecto da exibição que você deseja localizar. Em seguida, altere a propriedade apropriada no dicionário de recursos e defina as propriedades. Lote as chamadas para o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método chamando o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de definir as propriedades e <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> depois de definir as propriedades.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
  
1. Compile a solução.  
  
     Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
2. Crie um arquivo de texto e digite algum texto.  
  
    - O cursor de inserção deve ser magenta e o cursor de substituição deve ser turquesa.  
  
    - A margem do indicador (à esquerda da exibição de texto) deve estar verde claro.  
  
3. Selecione o texto que você acabou de digitar. A cor do texto selecionado deve ser rosa claro.  
  
4. Enquanto o texto estiver selecionado, clique em qualquer lugar fora da janela de texto. A cor do texto selecionado deve ser rosa-escuro.  
  
5. Ative o espaço em branco visível. (No menu **Editar** , aponte para **avançado** e clique em **Exibir espaço em branco**). Digite algumas guias no texto. As setas vermelhas que representam as guias devem ser exibidas.  
  
## <a name="see-also"></a>Consulte Também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)
