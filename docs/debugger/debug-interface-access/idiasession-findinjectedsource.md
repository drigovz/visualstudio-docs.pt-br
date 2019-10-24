---
title: IDiaSession::findInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2145c90c25c448880e51b9b394c7085e0d49b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742251"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Recupera uma lista de fontes que foram colocadas no repositório de símbolos por provedores de atributos ou outros componentes do processo de compilação.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parâmetros
 srcFile

no Nome do arquivo de origem para pesquisa.

 ppResult

fora Retorna um objeto [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) que contém uma lista de todas as fontes injetadas.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)