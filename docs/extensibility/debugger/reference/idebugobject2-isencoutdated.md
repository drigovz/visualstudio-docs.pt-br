---
title: IDebugObject2::IsEncOutdated | Microsoft Docs
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
ms.openlocfilehash: 70c1af4a67c55189531c2826e9eb22f0482eb520
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413756"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método determina se o status de editar e continuar desse objeto ou do contêiner pai está desatualizado. Um avaliador de expressão personalizada não implementa esse método e sempre retorna `E_NOTIMPL`.  
  
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
 [out] Diferente de zero (`TRUE`) se o estado de editar e continuar está desatualizado, zero (`FALSE`) se não for.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
> [!NOTE]
> Um avaliador de expressão personalizada deve sempre retornar `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
