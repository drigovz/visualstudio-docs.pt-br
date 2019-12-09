---
title: IDiaSymbol::findChildrenExByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f791074d029be78eb7d45e06dce8a8cce145f71
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149998"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera os filhos do símbolo que são válidos em um endereço especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `symtag`  
 [in] Especifica as marcas de símbolo dos filhos a serem recuperados, conforme definido na [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Definido como `SymTagNull` para todos os filhos a serem recuperados.  
  
 `name`  
 [in] Especifica o nome dos filhos a serem recuperados. Definido como `NULL` para todos os filhos a serem recuperados.  
  
 `compareFlags`  
 [in] Especifica as opções de comparação a ser aplicado à correspondência de nomes. Os valores do [enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada sozinho ou em combinação.  
  
 `address`  
 [in] O endereço do símbolo.  
  
 `ppResult`  
 [out] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperado do objeto que contém uma lista dos símbolos de filho.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se pelo menos um filho do símbolo foi encontrado ou retorna `S_FALSE` se nenhum filho foram encontrado; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os símbolos de locais que são retornados incluem informações de intervalo em tempo real.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
