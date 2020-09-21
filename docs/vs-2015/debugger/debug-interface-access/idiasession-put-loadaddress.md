---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838261"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Define o endereço de carregamento para o arquivo executável que corresponde aos símbolos neste repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `NewVal`  
 no Carregue o endereço para o arquivo executável.  
  
## <a name="remarks"></a>Comentários  
 As propriedades de endereço virtual de símbolo (VA) são computadas usando o valor desse método. Os endereços virtuais não são calculados, a menos que essa propriedade seja definida como diferente de zero.  
  
> [!NOTE]
> Você deve chamar esse método quando obter o objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e antes de começar a usar o objeto se precisar usar qualquer propriedade virtual em símbolos.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
