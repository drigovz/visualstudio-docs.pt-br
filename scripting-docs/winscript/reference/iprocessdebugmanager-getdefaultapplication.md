---
title: 'IProcessDebugManager:: GetDefaultApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576792"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Retorna um objeto de aplicativo padrão para o processo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppda`  
 fora O objeto de aplicativo de depuração para este aplicativo.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um novo objeto Depurar aplicativo e o adiciona à lista aplicativo em execução, se necessário.  
  
 Os mecanismos de linguagem devem usar o aplicativo especificado pelo método `GetDefaultApplication` se estiverem em execução em um host que não forneça um aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)