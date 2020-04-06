---
title: Fornecer suporte de delineamento em um serviço de idioma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707965"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Como: Fornecer suporte de delineamento expandido em um serviço de idioma legado
Existem duas opções para estender o suporte delineamento para o seu idioma além de apoiar o comando **Colapso para Definições.** Você pode adicionar regiões de contorno controladas pelo editor e adicionar regiões de contorno controladas pelo cliente.

## <a name="adding-editor-controlled-outline-regions"></a>Adicionando regiões de contorno controladas por editores
 Use essa abordagem para criar uma região de contorno e, em seguida, permitir que o editor para lidar com se a região é expandida, colapsado, e assim por diante. Das duas opções para fornecer suporte delineamento, esta opção é a menos robusta. Para esta opção, você cria uma nova região de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>contorno em uma extensão especificada de texto usando . Após a criação dessa região, seu comportamento é controlado pelo editor. Use o procedimento a seguir para implementar regiões de contorno controladas pelo editor.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar uma região de contorno controlada por editores

1. Chamada `QueryService` para<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Isso retorna um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>ponteiro para .

2. Chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando em um ponteiro para um determinado buffer de texto. Isso retorna um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> ponteiro para o objeto para o buffer.

3. Convoque <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>ponteiro para .

4. Chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para adicionar uma ou mais novas regiões de contorno de cada vez.

     Este método permite especificar o período de texto para delinear, se as regiões de contorno existentes são removidas ou preservadas, e se a região de contorno é expandida ou colapsada por padrão.

## <a name="add-client-controlled-outline-regions"></a>Adicionar regiões de contorno controladas pelo cliente
 Use essa abordagem para implementar delineamento controlado pelo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] cliente [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (ou inteligente) como o usado pelos serviços de idioma. Um serviço de idiomas que gerencia seu próprio delineamento monitora o conteúdo do buffer de texto, a fim de destruir regiões de contorno antigas quando elas se tornam inválidas e criar novas regiões de contorno conforme necessário.

### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar uma região de contorno controlada pelo cliente

1. Chamada `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>para . Isso retorna um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>ponteiro para .

2. Chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando em um ponteiro para um determinado buffer de texto. Isso determina se já existe uma sessão de texto oculta para o buffer.

3. Se uma sessão de texto já existir, então você não precisa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> criar uma, e um ponteiro para o objeto existente é devolvido. Use este ponteiro para enumerar e criar regiões de contorno. Caso contrário, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> chame para criar uma sessão de texto oculta para o buffer. Um ponteiro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para o objeto é devolvido.

    > [!NOTE]
    > Quando você <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>liga, você pode especificar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> cliente de texto oculto (ou seja, um objeto). Esse cliente notifica você quando um texto oculto ou região de contorno é expandido ou colapsado pelo usuário.

4. Estrutura <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> de chamada) parâmetro: <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> Especifique um valor no `iType` membro da <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura para indicar que você está criando uma região de contorno, em vez de uma região oculta. Especifique se a região é controlada `dwBehavior` pelo <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> cliente ou controlada pelo editor no membro da estrutura. Sua implementação de delineamento inteligente pode conter uma mistura de regiões de contorno controladas pelo editor e pelo cliente. Especifique o texto do banner exibido quando a região do `pszBanner` contorno <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> é colapsada, como "...", no membro da estrutura. O texto de banner padrão do editor para uma região oculta é "...".
