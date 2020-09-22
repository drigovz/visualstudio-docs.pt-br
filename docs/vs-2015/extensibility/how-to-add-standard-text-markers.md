---
title: Como adicionar marcadores de texto padrão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838278"
---
# <a name="how-to-add-standard-text-markers"></a>Como adicionar marcadores de texto padrão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use o procedimento a seguir para criar um dos tipos de marcador de texto padrão fornecidos com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor de núcleo.  
  
### <a name="to-create-a-text-marker"></a>Para criar um marcador de texto  
  
1. Dependendo se você estiver usando um sistema de coordenadas de um ou dois dimensional, chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para criar um novo marcador de texto.  
  
     Nessa chamada de método, especifique um tipo de marcador, um intervalo de texto para o qual criar o marcador e uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface. Esse método retorna um ponteiro para o marcador de texto recém-criado. Os tipos de marcador são extraídos da <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> enumeração. Especifique uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface se desejar ser informado de eventos de marcador.  
  
    > [!NOTE]
    > Crie marcadores de texto somente no thread da interface do usuário principal. O editor principal depende do conteúdo do buffer de texto para criar marcadores de texto e o buffer de texto não é thread-safe.  
  
## <a name="adding-a-custom-command"></a>Adicionando um comando personalizado  
 A implementação da `IVsTextMarkerClient` interface e o fornecimento de um ponteiro para ela de um marcador aprimora o comportamento do marcador de várias maneiras. Primeiro, isso permite que você forneça dicas para o marcador e execute comandos. Isso também permite que você receba notificações de eventos para marcadores individuais e crie um menu de contexto personalizado sobre o marcador. Use o procedimento a seguir para adicionar um comando personalizado ao menu de contexto do marcador.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Para adicionar um comando personalizado ao menu de contexto  
  
1. Antes de o menu de contexto ser exibido, o ambiente chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> método e passa um ponteiro para o marcador de texto afetado e o número do item de comando no menu de contexto.  
  
     Por exemplo, os comandos específicos de ponto de interrupção no menu de contexto incluem **remover o ponto** de interrupção por meio do **novo ponto de interrupção**, conforme exibido na captura de tela a seguir.  
  
     ![Menu de contexto do marcador](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Retorne algum texto identificando o nome do comando personalizado. Por exemplo, **remover ponto de interrupção** pode ser um comando personalizado se o ambiente ainda não o forneceu. Você também retorna se o comando tem suporte, está disponível e habilitado e/ou uma alternância de desligamento. O ambiente usa essas informações para exibir o comando personalizado no menu de contexto da maneira correta.  
  
3. Para executar o comando, o ambiente chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> método, passando um ponteiro para o marcador de texto e o número do comando selecionado no menu de contexto.  
  
     Use essas informações desta chamada para executar quaisquer ações do marcador de texto que o comando personalizado determinar.  
  
## <a name="see-also"></a>Consulte Também  
 [Usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)   
 [Como criar marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)   
 [Como usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
