---
title: Objeto VSTextBuffer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690637"
---
# <a name="vstextbuffer-object"></a>Objeto VSTextBuffer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O objeto de buffer de texto representa um fluxo de texto em Unicode, que é geralmente associado um arquivo. Um <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto pode ser usado fora do contexto do editor de núcleo, como no caso de um assistente.  
  
 A tabela a seguir mostra as interfaces de `VSTextBuffer`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interface OLE padrão. Usado principalmente para tratamento no buffer de desfazer/refazer.|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interface OLE padrão.|  
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações de compostos (ou seja, ações que são agrupadas em uma unidade de desfazer/refazer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita a persistência de dados do documento gerenciados pelo buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Usado para pesquisar um buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece ler e gravar recursos usando as coordenadas bidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece ler e gravar recursos usando coordenadas unidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápido e fornece acesso sequencial orientada por fluxo para o texto no buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome ou o moniker do buffer. Você pode armazenar seus próprios dados aleatórios em buffer com essa interface criando um GUID e usá-lo como uma chave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Dá suporte a pontos de conexão para eventos.|  
  
## <a name="remarks"></a>Comentários  
 O `VSTextBuffer` costuma ser encontrado por um `QueryInterface` chamar em `IVsTextBuffer`. Para obter mais informações, consulte [Buffer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edição de figuras](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
