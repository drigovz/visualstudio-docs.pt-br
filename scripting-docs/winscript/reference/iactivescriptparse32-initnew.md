---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
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
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561652"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicializa o mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se tiver êxito ou `E_FAIL` se ocorrer um erro durante a inicialização.  
  
## <a name="remarks"></a>Comentários  
 Antes que o mecanismo de script possa ser usado, um dos seguintes métodos deve ser chamado: `IPersist*::Load`, `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew`. A semântica desse método é idêntica à `IPersistStreamInit::InitNew`, pois esse método diz ao mecanismo de script para se inicializar. Observe que não é válido chamar `IPersist*::InitNew` ou `IActiveScriptParse32::InitNew` e `IPersist*::Load`, nem é válido chamar `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` ou `IPersist*::Load` mais de uma vez.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)