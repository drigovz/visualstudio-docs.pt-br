---
title: 'IDiaStackFrame:: get_lengthParams | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthParams method
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 079e510a5cf01d17251a8933448ca479f5f93041
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563504"
---
# <a name="idiastackframeget_lengthparams"></a>IDiaStackFrame::get_lengthParams
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o número de bytes de parâmetros enviados por push na pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o número de bytes de parâmetros.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se a propriedade não tem suporte. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
