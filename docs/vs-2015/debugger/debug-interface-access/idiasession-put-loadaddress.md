---
title: 'Idiasession:: Put_loadaddress | Microsoft Docs'
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
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5451eb14ab25a4f86acfa2870d30b91cf2751ee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847663"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Define o endereço de carregamento para o arquivo executável que corresponde aos símbolos nesse repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `NewVal`  
 [in] Carregar o endereço para o arquivo executável.  
  
## <a name="remarks"></a>Comentários  
 Propriedades de endereço virtual (VA) de símbolo são calculadas usando o valor desse método. Endereços virtuais não são calculados, a menos que essa propriedade é definida como diferente de zero.  
  
> [!NOTE]
>  Você deve chamar esse método quando você receber o [IDiaSession](../../debugger/debug-interface-access/idiasession.md) do objeto e antes de começar a usar o objeto se você precisar usar quaisquer propriedades virtuais nos símbolos.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



