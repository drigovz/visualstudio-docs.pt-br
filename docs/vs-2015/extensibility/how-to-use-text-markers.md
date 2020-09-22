---
title: Como usar marcadores de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838435"
---
# <a name="how-to-use-text-markers"></a>Como usar marcadores de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Marcadores de texto podem ser aplicados para editar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-apply-text-markers"></a>Para aplicar marcadores de texto  
  
1. Obtenha uma instância da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> classe.  
  
    > [!NOTE]
    > O editor central aplica automaticamente marcadores de texto padrão a qualquer documento que esteja editando e não deve ser necessário aplicar marcadores de texto padrão explicitamente.  
  
2. Obtenha uma ID de tipo de marcador do marcador no qual você está interessado chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método com o `GUID` do marcador de texto com o qual você deseja trabalhar.  
  
    > [!NOTE]
    > Não use o `GUID` do VSPackage ou do serviço que fornece o marcador de texto.  
  
3. Use a ID de tipo de marcador obtida chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> método como um parâmetro para chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método para aplicar um marcador de texto a uma determinada região de texto.  
  
#### <a name="to-add-features-to-text-markers"></a>Para adicionar recursos a marcadores de texto  
  
1. Pode ser desejável adicionar recursos adicionais a um marcador de texto, como dicas de ferramenta, um menu de contexto especial ou um manipulador para circunstâncias especiais. Para fazer isso:  
  
2. Crie um objeto que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
3. Se a funcionalidade adicional for desejada, implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> e as <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfaces no mesmo objeto que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface.  
  
4. Passe a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface que você cria, para a chamada para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método ou para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> método usado para aplicar o marcador de texto a uma determinada região de texto.  
  
5. Ao adicionar o suporte ao menu de contexto a uma região de marcador de texto, é necessário criar o menu.  
  
     Para obter mais informações sobre como criar um menu de contexto, consulte [menus de contexto](../extensibility/context-menus.md).  
  
6. O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente chama os métodos das interfaces fornecidas, como o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> método, ou o método, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> conforme necessário.  
  
## <a name="see-also"></a>Consulte Também  
 [Usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como criar marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)   
 [Como implementar o marcador de erros](../extensibility/how-to-implement-error-markers.md)
