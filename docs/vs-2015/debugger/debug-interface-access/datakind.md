---
title: DataKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922252"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica o escopo específico de um valor de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementos  
 DataIsUnknown  
 Símbolo de dados não pode ser determinado.  
  
 DataIsLocal  
 Item de dados é uma variável local.  
  
 DataIsStaticLocal  
 Item de dados é uma variável local estática.  
  
 DataIsParam  
 Item de dados é um parâmetro formal.  
  
 DataIsObjectPtr  
 Item de dados é um ponteiro de objeto (`this`).  
  
 DataIsFileStatic  
 Item de dados é uma variável no escopo do arquivo.  
  
 DataIsGlobal  
 Item de dados é uma variável global.  
  
 DataIsMember  
 Item de dados é uma variável de membro de objeto.  
  
 DataIsStaticMember  
 Item de dados é uma variável de classe estática.  
  
 DataIsConstant  
 Item de dados é um valor constante.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados pelo [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
