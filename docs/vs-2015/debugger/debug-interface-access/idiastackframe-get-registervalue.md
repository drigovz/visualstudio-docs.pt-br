---
title: 'Idiastackframe:: Get_registervalue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8038acf2aef8c34d07e7f21543a597ad7b96fa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923580"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o valor de um registro especificado conforme armazenado no quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `registerIndex`  
 [in] Um dos [enumeração CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) valores de enumeração.  
  
 `pRetVal`  
 [out] Valor armazenado no registro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Enumeração CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
