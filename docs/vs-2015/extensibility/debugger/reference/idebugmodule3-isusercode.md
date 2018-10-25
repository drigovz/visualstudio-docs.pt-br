---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06876664ea0bcc3ead15496905067e0c0aadf6ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833974"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera informações sobre se o módulo representa o código do usuário ou não.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfUser`  
 [out] Diferente de zero (`TRUE`) se o módulo representa o código do usuário, zero (`FALSE`) se não existir.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

