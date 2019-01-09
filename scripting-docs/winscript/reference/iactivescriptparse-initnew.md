---
title: 'Iactivescriptparse:: Initnew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f0998bea50d7839f93111aa6b116934fae35bfa3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089980"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicializa o mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_FAIL` se ocorreu um erro durante a inicialização.  
  
## <a name="remarks"></a>Comentários  
 Antes do mecanismo de script pode ser usado, um dos métodos a seguir deve ser chamado: `IPersist*::Load`, `IPersist*::InitNew`, ou `IActiveScriptParse::InitNew`. A semântica desse método é idêntica aos `IPersistStreamInit::InitNew`, em que esse método informa ao mecanismo de script para se inicializar. Observe que não é válido chamar ambos `IPersist*::InitNew` ou `IActiveScriptParse::InitNew` e `IPersist*::Load`, não é válido chamar `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, ou `IPersist*::Load` mais de uma vez.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)