---
title: 'Idiasectioncontrib:: Get_discardable | Microsoft Docs'
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
- IDiaSectionContrib::get_discardable method
ms.assetid: 30ca88d4-3198-4b0f-b30e-2e54b3607fe9
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e065a887ea34a124efef13f0f02c3f850e8c32e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201312"
---
# <a name="idiasectioncontribgetdiscardable"></a>IDiaSectionContrib::get_discardable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um sinalizador que indica se a seção pode ser descartada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_discardable (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se a seção pode ser descartada da memória conforme necessário; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



