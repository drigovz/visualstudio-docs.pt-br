---
title: NameSearchOptions | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b3e29ece07ffb385da0c54a3f8f4d31afc60be7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199219"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica as opções de pesquisa para nomes de arquivo e símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum NameSearchOptions {   
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
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession:: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



