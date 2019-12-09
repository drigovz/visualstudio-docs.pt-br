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
ms.openlocfilehash: ca1b1ec2bea56ad167951ad8b60cf849bd22e315
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742794"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lê o número especificado de bytes começando no endereço virtual relativo (RVA) especificado do arquivo executável.

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

no O RVA no arquivo executável para começar a ler.

 `cbData`

no Número de bytes a serem lidos.

 `pcbData`

fora Retorna o número de bytes lidos.

 `data[]`

[entrada, saída] Uma matriz que é preenchida com bytes lidos do arquivo.

## <a name="remarks"></a>Comentários
 Esse método é chamado pelo código de suporte do DIA para carregar bytes de dados de um executável usando um endereço virtual relativo. Esse método é chamado no suporte do método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Consulte também
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)