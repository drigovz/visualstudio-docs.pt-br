---
title: 'IDebugObject2:: isuserdata | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd595ce041ae1968e085e3b63b49d308cfd14452
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194586"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se o objeto representa dados do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfUser`  
 fora Retorna zero ( `TRUE` ) se o objeto representar dados do usuário; zero ( `FALSE` ) se não tiver.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os dados do usuário são qualquer objeto que faça parte de um módulo designado como JustMyCode (uma opção configurável pelo usuário que marca um módulo como código do usuário e, portanto, visível em um rastreamento de pilha).  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
