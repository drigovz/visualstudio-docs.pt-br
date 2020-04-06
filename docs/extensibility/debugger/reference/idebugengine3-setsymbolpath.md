---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730666"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Define os caminhos ou caminhos pesquisados para depurar símbolos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>parâmetros

`szSymbolSearchPath`\
[em] String contendo o caminho de pesquisa do símbolo ou caminhos. Consulte "Observações" para obter detalhes. Não pode ser nulo.

`szSymbolCachePath`\
[em] String contendo o caminho local onde os símbolos podem ser armazenados em cache. Não pode ser nulo.

`Flags`\
[em] Não utilizado; sempre definido para 0.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A `szSymbolSearchPath` string é uma lista de um ou mais caminhos, separados por ponto e vírgula, para procurar símbolos. Esses caminhos podem ser um caminho local, um caminho no estilo UNC ou uma URL. Esses caminhos também podem ser uma mistura de diferentes tipos. Se o caminho for UNC \\(por exemplo, \Symserver\Symbols), então o mecanismo de depuração deve determinar se o caminho é para um `szSymbolCachePath`servidor de símbolos e deve ser capaz de carregar símbolos desse servidor, cacheando-os no caminho especificado por .

 O caminho do símbolo também pode conter um ou mais locais de cache. Os caches são listados em ordem prioritária, com o cache de maior prioridade primeiro e separados por símbolos *. Por exemplo:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 O método [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) executa a carga real dos símbolos.

## <a name="see-also"></a>Confira também
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
