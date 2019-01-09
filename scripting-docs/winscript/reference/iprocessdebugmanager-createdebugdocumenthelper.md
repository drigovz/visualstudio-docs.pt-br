---
title: 'Iprocessdebugmanager:: Createdebugdocumenthelper | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62f61f00d2b5f850848efbcf3df65c5a3b10de3c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090477"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Cria um novo auxiliar de documento de depuração para este aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `punkOuter`  
 [in] Se o objeto retornado deve ser agregada, `punkOuter` é um ponteiro de interface para o controle `IUnknown`. Caso contrário, ele é um ponteiro nulo.  
  
 `pddh`  
 [out] O objeto documento auxiliar de depuração para este aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um novo auxiliar de documento de depuração para este aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)