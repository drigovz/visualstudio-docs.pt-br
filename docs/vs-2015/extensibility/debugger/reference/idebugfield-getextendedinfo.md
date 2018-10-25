---
title: IDebugField::GetExtendedInfo | Microsoft Docs
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
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30bc444b82f81bac44286893cabc674885e25206
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911558"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método obtém informações estendido sobre um campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidExtendedInfo`  
 [in] Seleciona as informações a serem retornados. Os valores válidos são:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`guidConstantValue`|O valor como uma sequência de bytes.|  
|`guidConstantType`|O tipo como uma assinatura de tipo.|  
  
 `prgBuffer`  
 [out] Retorna as informações estendidas.  
  
 `pdwLen`  
 [no, out] Retorna o tamanho das informações estendidas, em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Atualmente, esse método retorna apenas o tipo ou valor de uma constante. O chamador deve liberar o buffer retornado no `prgBuffer` chamando do COM `CoTaskMemFree` função (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

