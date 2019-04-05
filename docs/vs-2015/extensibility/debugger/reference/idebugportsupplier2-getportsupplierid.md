---
title: IDebugPortSupplier2::GetPortSupplierId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9b8e1db99727427e18a12b5d159c61212f706be
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928186"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o identificador de fornecedor de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetPortSupplierId(   
   GUID* pguidPortSupplier  
);  
```  
  
```csharp  
HRESULT GetPortSupplierId(   
   out Guid pguidPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pguidPortSupplier`  
 [out] Retorna o GUID do fornecedor de porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
