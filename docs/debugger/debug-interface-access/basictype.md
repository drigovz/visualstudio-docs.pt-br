---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 891b83d6a43cb73fe8f38bb8b20201cbcfa230f6
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154076"
---
# <a name="basictype"></a>BasicType
Especifica o tipo básico do símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
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
   btHresult  = 31,  
   btChar16   = 32,  // char16_t
   btChar32   = 33,  // char32_t
};  
```  
  
## <a name="elements"></a>Elementos  
 btNoType  
 Nenhum tipo básico é especificado.  
  
 btVoid  
 Tipo básico é um `void`.  
  
 btChar  
 Tipo básico é um `char` (tipo de C/C++).  
  
 btWChar  
 Tipo básico é um caractere largo de (Unicode) (`WCHAR`).  
  
 btInt  
 Tipo básico é `signed int` (tipo de C/C++).  
  
 btUInt  
 Tipo básico é `unsigned int` (tipo de C/C++).  
  
 btFloat  
 Tipo básico é um número de ponto flutuante (`FLOAT`).  
  
 btBCD  
 Tipo básico é um decimal codificado binário (`BCD`).  
  
 btBool  
 Tipo básico é um valor booliano (`BOOL`).  
  
 btLong  
 Tipo básico é um `long int` (tipo de C/C++).  
  
 btULong  
 Tipo básico é um `unsigned long int` (tipo de C/C++).  
  
 btCurrency  
 Tipo básico é a moeda.  
  
 btDate  
 Tipo básico é de data/hora (`DATE`).  
  
 btVariant  
 Tipo básico é uma estrutura de tipo de variável (`VARIANT`).  
  
 btComplex  
 Tipo básico é um número complexo.  
  
 btBit  
 Tipo básico é um pouco.  
  
 btBSTR  
 Tipo básico é uma cadeia de caracteres básica ou binary (`BSTR`).  
  
 btHresult  
 Tipo básico é um `HRESULT`.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados pelo [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
