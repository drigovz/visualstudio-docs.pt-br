---
title: 'Idiasession:: Findlines | Microsoft Docs'
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
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 087248b4d4f25847fa8896a6896c335e2751b906
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910739"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera os números de linha dentro de compiland especificado e identificadores de arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `compiland`  
 [in] Uma [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o compiland. Use esta interface como um contexto no qual pesquisar os números de linha.  
  
 `file`  
 [in] Uma [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto que representa o arquivo de origem no qual pesquisar os números de linha.  
  
 `ppResult`  
 [out] Retorna um [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) recuperado do objeto que contém uma lista dos números de linha.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



