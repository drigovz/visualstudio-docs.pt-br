---
title: Forneça suporte de texto oculto no serviço de idioma legado
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707923"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Como: Fornecer suporte a texto oculto em um serviço de idioma legado
Você pode criar regiões de texto ocultas, além de delinear regiões. As regiões de texto ocultas podem ser controladas pelo cliente ou controladas pelo editor e são usadas para ocultar uma região de texto completamente. O editor exibe uma região oculta como linhas horizontais. Um exemplo disso é a exibição **Script Only** no editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Para implementar uma região de texto oculto

1. Chamada `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>para .

     Isso retorna um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>ponteiro para .

2. Chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando em um ponteiro para um determinado buffer de texto. Isso determina se já existe uma sessão de texto oculta para o buffer.

3. Se um já existe, então você não precisa criar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> e um ponteiro para o objeto existente é devolvido. Use este ponteiro para enumerar e criar regiões de texto ocultas. Caso contrário, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> chame para criar uma sessão de texto oculta para o buffer.

     Um ponteiro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para o objeto é devolvido.

    > [!NOTE]
    > Quando você `CreateHiddenTextSession`liga, você pode especificar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>cliente de texto oculto (isto é, ). O cliente de texto oculto notifica você quando o texto oculto ou o delineamento é expandido ou colapsado pelo usuário.

4. Chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> para adicionar uma ou mais novas regiões de contorno `reHidReg` de<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>cada vez, especificando as seguintes informações no parâmetro ( )

    1. Especifique `hrtConcealed` um `iType` valor <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> no membro da estrutura para indicar que você está criando uma região oculta, em vez de uma região de contorno.

        > [!NOTE]
        > Quando as regiões ocultas são ocultas, o editor exibe automaticamente linhas ao redor das regiões ocultas para indicar sua presença.

    2. Especifique se a região é controlada `dwBehavior` pelo <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> cliente ou controlada pelo editor nos membros da estrutura. Sua implementação de delineamento inteligente pode conter uma mistura de regiões de contorno controladas por editor esboçar e texto oculto.
