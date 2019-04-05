---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29b6500ab138883c8cbf71eda5a0afad1329494e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922337"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica as opções de pesquisa para nomes de arquivo e símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elementos  
 `nsNone`  
 Nenhuma opção foi especificada.  
  
 `nsfCaseSensitive`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas.  
  
 `nsfCaseInsensitive`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas.  
  
 `nsfFNameExt`  
 Trata nomes como caminhos e aplica-se uma correspondência de nome de arquivo filename. ext.  
  
 `nsfRegularExpression`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas usando asteriscos (*) e pontos de interrogação (?) como caracteres curinga.  
  
 `nsfUndecoratedName`  
 Aplica-se apenas aos símbolos que têm não decorados e nomes decorados.  
  
## <a name="remarks"></a>Comentários  
 Os valores dessa enumeração são passados para os seguintes métodos:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
