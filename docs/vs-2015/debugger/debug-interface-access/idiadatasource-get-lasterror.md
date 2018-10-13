---
title: 'Idiadatasource:: Get_lasterror | Microsoft Docs'
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
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c6824d651cc56aa56d027996abf6b76107adf30
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302998"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o nome do arquivo para o último erro de carregamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pRetVal  
 [out] Retorna uma cadeia de caracteres que contém o nome do arquivo. PDB associado com o último erro de carregamento.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o último código de erro causado por uma operação de carregamento. Retorna `E_INVALIDARG` se o `pRetVal` parâmetro é `NULL`.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)



