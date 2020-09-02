---
title: Barra suspensa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204660"
---
# <a name="drop-down-bar"></a>Barra suspensa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A barra suspensa é fornecida na parte superior da janela de código e contém duas listas suspensas.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de barras suspensas  
 No [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , por exemplo, a barra suspensa contém listas para [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] itens e [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] funções membros de itens, conforme mostrado na imagem a seguir.  
  
 ![Remover barras de&#45;para baixo](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Barra suspensa  
  
 Ao implementar uma barra suspensa, há quatro interfaces de importância primária:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implemente essa interface para inserir o conteúdo da barra suspensa. Cada combinação suspensa pode conter texto sem formatação ou um texto decorativo (negrito, sublinhado ou itálico), pode ter cores de fonte de texto de janela ou cores de fonte esmaecidas e, opcionalmente, fornecer um bitmap pequeno ao lado do item suspenso. Semelhante à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface, as imagens de bitmap são fornecidas em listas de imagens. Cada combinação suspensa pode ter uma lista de imagens diferente; no entanto, cada lista de imagens deve conter imagens da mesma altura. Além disso, usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> método, você pode fornecer uma dica de ferramenta para cada combinação.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Chame essa interface para criar ou destruir a barra suspensa de uma janela de código. Essa interface também pode ser usada para determinar se uma barra suspensa já está anexada a uma janela de código chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método. Chamada <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Chame essa interface para se comunicar diretamente com a barra suspensa. Você pode usar essa interface para forçar uma atualização do conteúdo da barra suspensa ou para alterar a seleção em uma das caixas de listagem.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Se você registrou o `ShowDropdownBarOption` em sua chave de registro de serviço de idioma, o Gerenciador de janela de código deve monitorar esse evento para sincronizar com as preferências do usuário em relação a se a barra suspensa deve ser exibida. Se você não registrar essa opção em sua chave de serviço de idioma, a opção para mostrar ou ocultar a barra suspensa será desabilitada no menu de **Opções** .  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Anexando uma barra suspensa a uma janela de código  
 Para anexar uma barra suspensa à janela de código quando ela é criada, um serviço de idioma deve ser anexado à barra suspensa quando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> método é chamado. Se uma chamada para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método indicar que uma barra suspensa ainda não existe, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Para acessar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interface, chame <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ponteiro retornado para você quando sua <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementação foi anexada.  
  
## <a name="see-also"></a>Consulte Também  
 [Personalizando janelas de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Suporte para a barra de navegação em um serviço de linguagem herdado](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
