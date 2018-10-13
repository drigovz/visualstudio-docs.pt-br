---
title: Função CvInitProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa41b1cbbba6e88a86ae5af0c471d5f6627dcca2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276205"
---
# <a name="cvinitprovider-function"></a>Função CvInitProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicializa o provedor de marcador. Deve ser chamado antes das outras funções do SDK da Visualização Simultânea.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pGuid`  
 GUID do provedor. Não pode ser NULL.  
  
 `ppProvider`  
 Endereço de uma variável de saída que armazenará o contexto de provedor. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK quando o provedor é inicializado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)



