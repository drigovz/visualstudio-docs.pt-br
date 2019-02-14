---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42cfe138aa6be00628d319f01e7cccfbb4cc4f8a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040158"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Especifica o tipo de memória para acessar.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `MemTypeCode`  
 Acessos de memória somente código.  
  
 `MemTypeData`  
 Memória de dados ou a pilha de acessos.  
  
 `MemTypeStack`  
 Acessos apenas memória de pilha.  
  
 `MemTypeAny`  
 Acessa qualquer tipo de memória.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são passados para o [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) método para limitar o acesso a diferentes tipos de memória.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)