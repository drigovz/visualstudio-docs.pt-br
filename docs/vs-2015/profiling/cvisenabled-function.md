---
title: Função CvIsEnabled | Microsoft Docs
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
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4349d42309482622ae57ba27bb3e675bbdd6a403
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222463"
---
# <a name="cvisenabled-function"></a>Função CvIsEnabled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Determina se uma sessão habilitou o provedor ETW especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `category`  
 Categoria.  
  
 `level`  
 Nível de importância.  
  
 `pProvider`  
 Objeto de provedor válido. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o provedor estiver habilitado no momento. S_FALSE se o provedor estiver desabilitado no momento. Código de erro em caso de erros. Use a macro FAILED para verificar a condição de erro e depois verifique se S_OK/S_FALSE.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)



