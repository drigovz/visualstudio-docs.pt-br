---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150432"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera todos os filhos de um identificador pai especificado que correspondem ao nome e ao tipo de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `parent`  
 no Um objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o pai. Se esse símbolo pai for uma função, módulo ou bloco, seus filhos léxicos serão retornados em `ppResult` . Se o símbolo pai for um tipo, sua classe filho será retornada. Se esse parâmetro for `NULL` , `symtag` deve ser definido como `SymTagExe` ou `SymTagNull` , que retorna o escopo global (arquivo. exe).  
  
 `symtag`  
 no Especifica a marca de símbolo dos filhos a serem recuperados. Os valores são obtidos da enumeração de [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) . Defina como `SymTagNull` para recuperar todos os filhos.  
  
 `name`  
 no Especifica o nome dos filhos a serem recuperados. Defina como `NULL` para todos os filhos a serem recuperados.  
  
 `compareFlags`  
 no Especifica as opções de comparação aplicadas à correspondência de nomes. Os valores da enumeração de [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) podem ser usados sozinhos ou em combinação.  
  
 `ppResult`  
 fora Retorna um objeto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contém a lista de símbolos filho recuperados.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como localizar variáveis locais da função `pFunc` que correspondem ao nome `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Sobre](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
