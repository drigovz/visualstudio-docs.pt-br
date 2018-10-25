---
title: IDebugMethodField::GetThis | Microsoft Docs
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
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d942fab313e54497919de03081e7a47aff69ac7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888795"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o `this` (`Me` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ponteiro do objeto que contém o método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClass`  
 [out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que representa o ponteiro "this".  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em linguagens orientadas a objeto, normalmente há um ponteiro implícito para a instanciação atual de uma classe. Isso é conhecido como `this` no # C / C++ e assim como acontece `Me` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

