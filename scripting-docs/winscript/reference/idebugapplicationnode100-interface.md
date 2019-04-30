---
title: Interface IDebugApplicationNode100 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8de6f57cabe808df1506870fe65da31ef74e644
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436026"
---
# <a name="idebugapplicationnode100-interface"></a>Interface IDebugApplicationNode100
O `IDebugApplicationNode100` interface estende a funcionalidade dos [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md). Você pode obter uma instância dessa interface chamando QueryInterface em uma implementação de [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
> Essa interface é implementada pelo PDM v10.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 A interface `IDebugApplicationNode100` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Obtém os documentos de texto que estão ocultos, o filtro especificado.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Determina se o documento especificado pertence a um de nós filho deste nó.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Define o filtro em uma determinada [IDebugApplicationNodeEvents Interface](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementação. Ele permite que os depuradores de script filtrar os nós de aplicativo filho gerado pelo compilador para que o PDM não enviará mais eventos quando os nós são criados ou removidos. Por padrão, todos os nós serão enviados.|