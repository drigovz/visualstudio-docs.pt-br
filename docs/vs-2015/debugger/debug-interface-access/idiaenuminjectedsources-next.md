---
title: IDiaEnumInjectedSources::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d40ed9acf9e8c82fa315517c0abc3eb6f6d3b036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580493"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um número especificado de fontes injetadas na sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 no O número de fontes injetadas no enumerador a ser recuperado.  
  
 rgelt  
 fora Retorna uma matriz de objetos [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) que representa as fontes injetadas desejadas.  
  
 pceltFetched  
 fora Retorna o número de fontes injetadas no enumerador obtido.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver mais fontes injetadas. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
