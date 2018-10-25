---
title: 'Idiaenumframedata:: clone | Microsoft Docs'
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
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49bd2180344984203c568e40db3b0cdb68b8fb68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817009"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ppenum  
 [out] Retorna um [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) objeto que contém uma duplicata do enumerador. O quadro de dados não são duplicados, apenas o enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)



