---
title: 'IActiveScriptParse:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573505"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicializa o mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se tiver êxito ou `E_FAIL` se ocorrer um erro durante a inicialização.  
  
## <a name="remarks"></a>Comentários  
 Antes que o mecanismo de script possa ser usado, um dos seguintes métodos deve ser chamado: `IPersist*::Load`, `IPersist*::InitNew` ou `IActiveScriptParse::InitNew`. A semântica desse método é idêntica à `IPersistStreamInit::InitNew`, pois esse método diz ao mecanismo de script para se inicializar. Observe que não é válido chamar `IPersist*::InitNew` ou `IActiveScriptParse::InitNew` e `IPersist*::Load`, nem é válido chamar `IPersist*::InitNew`, `IActiveScriptParse::InitNew` ou `IPersist*::Load` mais de uma vez.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)