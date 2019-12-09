---
title: 'IPerPropertyBrowsing2:: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576768"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permite que o chamador Preencha uma caixa de listagem com uma matriz contada de ponteiros de cadeia de caracteres que representam valores potenciais para essa propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dispid`  
 no Identificador de expedição da propriedade para a qual o chamador está solicitando a lista de cadeias de caracteres.  
  
 `pCaStrings`  
 fora Ponteiro para uma estrutura de matriz contada e alocada pelo chamador que contém a contagem de elementos e o endereço de uma matriz alocada por método de ponteiros de cadeia de caracteres. Se o método falhar, nenhuma memória será alocada e o conteúdo da estrutura será indefinido.  
  
 `pCaCookies`  
 fora Ponteiro para a estrutura de matriz contada, atribuída pelo chamador, que contém a contagem de elementos e o endereço de uma matriz de DWORDs alocada por método. Se o método falhar, nenhuma memória será alocada e o conteúdo da estrutura será indefinido.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)