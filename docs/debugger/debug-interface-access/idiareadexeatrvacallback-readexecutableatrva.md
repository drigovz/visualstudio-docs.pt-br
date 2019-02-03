---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a075369a9064425bd0cffe096dbe96ca30b402
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999100"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lê o número especificado de bytes começando no especificado endereço virtual relativo (RVA) do arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
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