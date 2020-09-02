---
title: IDiaFrameData::get_maxStack | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bacefc74c4699ef2d2d75ff7ca7af47a56cfb44b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562882"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o número máximo de bytes enviados por push na pilha no quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o número máximo de bytes enviados por push na pilha.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O valor retornado por esse método normalmente é usado na interpretação de uma cadeia de caracteres de programa (consulte o método [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) para a definição de uma cadeia de caracteres de programa).  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
