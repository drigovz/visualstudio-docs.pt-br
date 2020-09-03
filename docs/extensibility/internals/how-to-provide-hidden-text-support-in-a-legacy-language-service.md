---
title: Fornecer suporte a texto oculto no serviço de linguagem herdado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707923"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Como fornecer suporte a texto oculto em um serviço de idioma herdado
Você pode criar regiões de texto ocultos, além de regiões de estrutura de tópicos. As regiões de texto ocultos podem ser controladas pelo cliente ou controladas pelo editor e usadas para ocultar completamente uma região de texto. O editor exibe uma região oculta como linhas horizontais. Um exemplo disso é a exibição **somente script** no editor de HTML.

## <a name="to-implement-a-hidden-text-region"></a>Para implementar uma região de texto oculta

1. Chamada `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando um ponteiro para um determinado buffer de texto. Isso determina se uma sessão de texto oculto já existe para o buffer.

3. Se já houver um, você não precisará criar um e um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto existente será retornado. Use esse ponteiro para enumerar e criar regiões de texto ocultos. Caso contrário, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para criar uma sessão de texto oculto para o buffer.

     Um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto é retornado.

    > [!NOTE]
    > Ao chamar `CreateHiddenTextSession` , você pode especificar um cliente de texto oculto (ou seja, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). O cliente de texto oculto notifica quando o texto oculto ou o contorno é expandido ou recolhido pelo usuário.

4. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> para adicionar uma ou mais novas regiões de estrutura de tópicos por vez, especificando as seguintes informações `reHidReg` no <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> parâmetro ():

    1. Especifique um valor de `hrtConcealed` no `iType` membro da <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura para indicar que você está criando uma região oculta, em vez de uma região de estrutura de tópicos.

        > [!NOTE]
        > Quando as regiões ocultas estão ocultas, o editor exibe automaticamente linhas em volta das regiões ocultas para indicar sua presença.

    2. Especifique se a região é controlada pelo cliente ou controlada pelo editor nos `dwBehavior` membros da <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura. Sua implementação de estrutura de tópicos inteligente pode conter uma combinação de estrutura de tópicos e regiões de texto ocultos e de editores controladas pelo cliente.
