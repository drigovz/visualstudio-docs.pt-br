---
title: 'IDebugObject2:: IsEncOutdated | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa4acd0476a0df75644738840da562db97a34bf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838394"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método determina se o status editar e continuar deste objeto ou do contêiner pai está desatualizado. Um avaliador de expressão personalizado não implementa esse método e sempre retorna `E_NOTIMPL` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfEncOutdated`  
 fora Diferente de zero ( `TRUE` ) se o estado editar e continuar estiver desatualizado, zero ( `FALSE` ) se não for.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
> [!NOTE]
> Um avaliador de expressão personalizado sempre deve retornar `E_NOTIMPL` .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
