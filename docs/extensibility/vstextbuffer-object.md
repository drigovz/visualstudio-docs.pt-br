---
title: Objeto VSTextBuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1895efa9ef10e1e554b98844619507224f09126
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189030"
---
# <a name="vstextbuffer-object"></a>Objeto VSTextBuffer
O objeto buffer de texto representa um fluxo de texto Unicode, que geralmente está associado a um arquivo. Um objeto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> pode ser usado fora do contexto do editor principal, como no, um assistente.

 A tabela a seguir mostra as interfaces de `VSTextBuffer`.

|Método|Descrição|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interface OLE padrão. Usado para a manipulação de desfazer/refazer no buffer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interface OLE padrão.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita a criação de ações de compostos (ou seja, ações agrupadas em uma única unidade de desfazer/refazer).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita a persistência de dados de documento gerenciados pelo buffer de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Usado para pesquisar um buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece recursos de leitura e gravação usando coordenadas bidimensionais. Herda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece recursos de leitura e gravação usando coordenadas unidimensionais. Herda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornece acesso seqüencial rápido, orientado a fluxo, ao texto no buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome, ou moniker, do buffer. Você pode armazenar seus próprios dados aleatórios no buffer com essa interface criando um GUID e usando-o como uma chave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Dá suporte a pontos de conexão para eventos.|

## <a name="remarks"></a>Comentários
 A `VSTextBuffer` geralmente é encontrada por uma chamada de `QueryInterface` no `IVsTextBuffer`. Para obter mais informações, consulte [buffer de texto](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)