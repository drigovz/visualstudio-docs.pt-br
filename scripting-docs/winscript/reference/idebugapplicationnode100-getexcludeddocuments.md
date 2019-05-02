---
title: IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8b1793fc1a3aacb27cc612bb5212dc33e7ab7dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436042"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
Obtém os documentos de texto que estão ocultos, o filtro especificado.  
  
> [!IMPORTANT]
> [Interface IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) é implementada pelo PDM v10.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `filter`  
 O filtro.  
  
 `pDocuments`  
 O conjunto de documentos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode100 Interface](../../winscript/reference/idebugapplicationnode100-interface.md)