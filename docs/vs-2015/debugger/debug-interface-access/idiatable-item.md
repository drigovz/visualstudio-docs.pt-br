---
title: 'IDiaTable:: item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574785"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera uma referência à entrada especificada na tabela.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `index`  
 no O índice da entrada da tabela no intervalo de 0 a `count` -1, em que `count` é retornado pelo método [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 fora Retorna um `IUnknown` objeto que representa a entrada da tabela especificada.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma tabela representa uma coleção de objetos. Dependendo desses objetos, o parâmetro do elemento pode ser convertido na interface apropriada. Por exemplo, se uma tabela contiver objetos [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , o parâmetro do elemento poderá ser convertido na `IDiaSegment` interface.  
  
 É uma abordagem mais comum para chamar o `QueryInterface` método na interface [IDiaTable](../../debugger/debug-interface-access/idiatable.md) para a interface do enumerador apropriada e usar os métodos específicos do enumerador para acessar o conteúdo da tabela. Consulte a interface [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) para obter um exemplo.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
