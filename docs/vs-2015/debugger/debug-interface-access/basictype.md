---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580831"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica o tipo básico do símbolo.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementos  
 btNoType  
 Nenhum tipo básico foi especificado.  
  
 btVoid  
 O tipo básico é um `void` .  
  
 btChar  
 O tipo básico é um `char` (tipo C/C++).  
  
 btWChar  
 O tipo básico é um caractere (Unicode) largo ( `WCHAR` ).  
  
 btInt  
 O tipo básico é `signed int` (tipo C/C++).  
  
 btUInt  
 O tipo básico é `unsigned int` (tipo C/C++).  
  
 btFloat  
 O tipo básico é um número de ponto flutuante ( `FLOAT` ).  
  
 btBCD  
 O tipo básico é um decimal codificado em binário ( `BCD` ).  
  
 btBool  
 O tipo básico é um booliano ( `BOOL` ).  
  
 btLong  
 O tipo básico é um `long int` (tipo C/C++).  
  
 btULong  
 O tipo básico é um `unsigned long int` (tipo C/C++).  
  
 btCurrency  
 O tipo básico é moeda.  
  
 btDate  
 O tipo básico é data/hora ( `DATE` ).  
  
 btVariant  
 O tipo básico é uma estrutura de tipo de variável ( `VARIANT` ).  
  
 btComplex  
 O tipo básico é um número complexo.  
  
 btBit  
 O tipo básico é um bit.  
  
 btBSTR  
 O tipo básico é uma cadeia de caracteres básica ou binária ( `BSTR` ).  
  
 btHresult  
 O tipo básico é um `HRESULT` .  
  
## <a name="remarks"></a>Comentários  
 Os valores nessa enumeração são retornados pelo método [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst. h  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
