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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197631"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica o escopo específico de um valor de dados.  
  
## <a name="syntax"></a>Syntax  
  
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
 O símbolo de dados não pode ser determinado.  
  
 DataIsLocal  
 O item de dados é uma variável local.  
  
 DataIsStaticLocal  
 O item de dados é uma variável local estática.  
  
 DataIsParam  
 O item de dados é um parâmetro formal.  
  
 DataIsObjectPtr  
 O item de dados é um ponteiro de objeto ( `this` ).  
  
 DataIsFileStatic  
 O item de dados é uma variável com escopo de arquivo.  
  
 DataIsGlobal  
 O item de dados é uma variável global.  
  
 DataIsMember  
 O item de dados é uma variável de membro de objeto.  
  
 DataIsStaticMember  
 O item de dados é uma variável estática de classe.  
  
 DataIsConstant  
 O item de dados é um valor constante.  
  
## <a name="remarks"></a>Comentários  
 Os valores nessa enumeração são retornados pelo método [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst. h  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
