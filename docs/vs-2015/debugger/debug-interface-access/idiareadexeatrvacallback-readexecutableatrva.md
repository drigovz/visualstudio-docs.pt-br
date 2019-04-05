---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928847"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lê o número especificado de bytes começando no especificado endereço virtual relativo (RVA) do arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `relativeVirtualAddress`  
 [in] O RVA no arquivo executável para iniciar a leitura.  
  
 `cbData`  
 [in] Número de bytes a serem lidos.  
  
 `pcbData`  
 [out] Retorna o número de bytes lidos.  
  
 `data[]`  
 [no, out] Uma matriz que é preenchida com bytes lidos do arquivo.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado pelo código de suporte do DIA para carregar os bytes de dados de um executável usando um endereço virtual relativo. Esse método é chamado suportados a [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
