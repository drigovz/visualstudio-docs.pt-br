---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547358"
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
