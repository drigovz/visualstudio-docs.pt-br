---
title: Informações de parâmetros em um serviço de linguagem legado1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706795"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informações de parâmetro em um serviço de linguagem herdado
A dica de ferramenta IntelliSense Parameter Info fornece aos usuários dicas sobre onde eles estão em uma construção de idioma.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Estendendo o Editor e os Serviços de Idiomas](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="how-parameter-info-tooltips-work"></a>Como funcionam as dicas de ferramentas de informações de parâmetros
 Quando você digita uma declaração no editor, o VSPackage exibe uma pequena janela de dica de ferramenta contendo a definição da declaração que está sendo digitada. Por exemplo, se você digitar uma declaração de `pMainFrame ->UpdateWindow`MFC (Microsoft Foundation Classes) (como) e pressionar a tecla de `UpdateWindow` abertura de parênteses para começar a listar parâmetros, uma dica de método aparecerá exibindo a definição do método.

 As dicas de ferramentas paraparâmetros info geralmente são usadas em conjunto com a conclusão da declaração. Eles são mais úteis para idiomas que têm parâmetros ou outras informações formatadas após o nome do método ou palavra-chave.

 As dicas de ferramentas Parâmetro Info são iniciadas pelo serviço de idiomas através de interceptação de comando. Para interceptar caracteres do usuário, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> seu objeto de serviço de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> idioma deve implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface e passar o texto para exibir um ponteiro para sua implementação, chamando o método na interface. O filtro de comando intercepta comandos que você digita na janela de código. Monitore as informações de comando para saber quando exibir informações de parâmetros ao usuário. Você pode usar o mesmo filtro de comando para conclusão de declaração, marcadores de erro e assim por diante.

 Quando você digita uma palavra-chave para a qual o serviço <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> de idioma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> pode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> fornecer dicas, então o serviço de idioma cria um objeto e chama o método na interface para notificar o IDE para exibir uma dica. Crie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> o `VSLocalCreateInstance` objeto usando e `CLSID_VsMethodTipWindow`especificando a coclasse . `VsLocalCreateInstance`é uma função definida no arquivo de cabeçalho vsdoc.h que solicita `QueryService` o registro local e chama `CreateInstance` este objeto para o `CLSID_VsMethodTipWindow`.

## <a name="providing-a-method-tip"></a>Fornecendo uma dica de método
 Para fornecer uma dica <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> de método, chame o método na interface, passando-lhe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> sua implementação da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface.

 Quando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> sua classe é invocada, seus métodos são chamados na seguinte ordem:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Retorna a posição e o comprimento dos dados relevantes no buffer de texto atual. Isso instrui o IDE a não obscurecer esses dados com a janela da dica de ferramenta.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Retorna o número do método (índice baseado em zero) que deseja ser exibido inicialmente. Por exemplo, se você retornar zero, então o primeiro método sobrecarregado é inicialmente apresentado.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Retorna o número de métodos sobrecarregados que são aplicáveis no contexto atual. Se você retornar um valor maior que 1 para este método, a exibição de texto será exibida para cima e para baixo setas para você. Se você clicar na seta para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> baixo, o IDE chamará o método. Se você clicar na seta para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> cima, o IDE chamará o método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     O texto da dica de ferramenta Parâmetro Info é <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> construído durante várias chamadas para os métodos.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Retorna o número de parâmetros a serem exibidos no método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Se você retornar um número de método correspondente à sobrecarga que deseja exibir, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> este método será chamado, seguido de uma chamada para o método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa seu serviço de idioma para atualizar o editor quando uma dica de método é exibida. No <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> método, chame o seguinte:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Você recebe uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> chamada para o método quando você fecha a janela de ponta do método.
