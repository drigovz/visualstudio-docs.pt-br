---
title: Como fornecer suporte expandido para estrutura de tópicos em um serviço de linguagem herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1b2fd8f3d7e4f3637957ef11c4acb20ba51261d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838748"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Como fornecer suporte estendido à estrutura de tópicos em um serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Há duas opções para estender o suporte à estrutura de tópicos para sua linguagem além de dar suporte ao comando **recolher para definições** . Você pode adicionar regiões de estrutura de tópicos controladas por editor e adicionar regiões de estrutura de tópicos controladas pelo cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Adicionando regiões de estrutura de tópicos controladas por editor  
 Use essa abordagem para criar uma região de estrutura de tópicos e, em seguida, permitir que o editor manipule se a região está expandida, recolhida e assim por diante. Das duas opções para fornecer suporte à estrutura de tópicos, essa opção é a menos robusta. Para essa opção, você cria uma nova região de estrutura de tópicos em um determinado trecho de texto usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Depois que essa região é criada, seu comportamento é controlado pelo editor. Use o procedimento a seguir para implementar regiões de estrutura de tópicos controladas por editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar uma região de estrutura de tópicos controlada por um editor  
  
1. Chamada `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .  
  
2. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando um ponteiro para um determinado buffer de texto. Isso retorna um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto para o buffer.  
  
3. Chamada <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .  
  
4. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para adicionar uma ou mais novas regiões de estrutura de tópicos por vez.  
  
     Esse método permite especificar o intervalo de texto a ser estruturado, se as regiões de estrutura de tópicos existentes são removidas ou preservadas, e se a região da estrutura de tópicos é expandida ou recolhida por padrão.  
  
## <a name="adding-client-controlled-outline-regions"></a>Adicionando regiões de estrutura de tópicos controladas pelo cliente  
 Use essa abordagem para implementar a estrutura de tópicos controlada pelo cliente (ou inteligente) como a usada pelos [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] serviços de linguagem e. Um serviço de linguagem que gerencia sua própria estrutura de tópicos monitora o conteúdo do buffer de texto para destruir regiões de estrutura de tópicos antigas quando elas se tornam inválidas e para criar novas regiões de estrutura de tópicos, conforme necessário.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar uma região de estrutura de tópicos controlada pelo cliente  
  
1. Chamada `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .  
  
2. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando um ponteiro para um determinado buffer de texto. Isso determina se uma sessão de texto oculto já existe para o buffer.  
  
3. Se uma sessão de texto já existir, você não precisará criar uma e um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto existente será retornado. Use esse ponteiro para enumerar e criar regiões de estrutura de tópicos. Caso contrário, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para criar uma sessão de texto oculto para o buffer. Um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto é retornado.  
  
    > [!NOTE]
    > Ao chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> , você pode especificar um cliente de texto oculto (ou seja, um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objeto). Esse cliente notifica quando um texto oculto ou uma região de estrutura de tópicos é expandida ou recolhida pelo usuário.  
  
4. Chamada de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> estrutura): especifique um valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> no `iType` membro da <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura para indicar que você está criando uma região de estrutura de tópicos, em vez de uma região oculta. Especifique se a região é controlada pelo cliente ou pelo editor no `dwBehavior` membro da <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura. Sua implementação de estrutura de tópicos inteligente pode conter uma mistura de regiões de estrutura de tópicos controladas por um editor e pelo cliente. Especifique o texto da faixa que será exibido quando a região da estrutura de tópicos for recolhida, como "...", no `pszBanner` membro da <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estrutura. O texto de faixa padrão do editor para uma região oculta é "...".
