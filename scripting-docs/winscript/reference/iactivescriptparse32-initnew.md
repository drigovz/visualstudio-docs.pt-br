---
title: IActiveScriptParse32::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 685c596caa61a5cbd5042fad3a1bfb39c349c1b1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094686"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicializa o mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_FAIL` se ocorreu um erro durante a inicialização.  
  
## <a name="remarks"></a>Comentários  
 Antes do mecanismo de script pode ser usado, um dos métodos a seguir deve ser chamado: `IPersist*::Load`, `IPersist*::InitNew`, ou `IActiveScriptParse32::InitNew`. A semântica desse método é idêntica aos `IPersistStreamInit::InitNew`, em que esse método informa ao mecanismo de script para se inicializar. Observe que não é válido chamar ambos `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew` e `IPersist*::Load`, não é válido chamar `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, ou `IPersist*::Load` mais de uma vez.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)