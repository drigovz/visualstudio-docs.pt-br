---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fe3000804971c8bd8cbf896a592bd11b875bfa8
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506386"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Define o caminho ou caminhos que são pesquisados para símbolos de depuração.

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
no Cadeia de caracteres que contém o caminho de pesquisa de símbolo ou caminhos. Consulte "Comentários" para obter detalhes. Não pode ser nulo.

`szSymbolCachePath`\
no Cadeia de caracteres que contém o caminho local onde os símbolos podem ser armazenados em cache. Não pode ser nulo.

`Flags`\
no Não usado; sempre definido como 0.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A cadeia de caracteres `szSymbolSearchPath` é uma lista de um ou mais caminhos, separados por ponto e vírgula, para procurar por símbolos. Esses caminhos podem ser um caminho local, um caminho de estilo UNC ou uma URL. Esses caminhos também podem ser uma combinação de tipos diferentes. Se o caminho for UNC (por exemplo, \\\Symserver\Symbols), o mecanismo de depuração deverá determinar se o caminho é para um servidor de símbolos e deve ser capaz de carregar símbolos desse servidor, armazenando-os no caminho especificado por `szSymbolCachePath`.

 O caminho do símbolo também pode conter um ou mais locais de cache. Os caches são listados em ordem de prioridade, com o cache de prioridade mais alta primeiro e separados por símbolos *. Por exemplo:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 O método [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) executa a carga real dos símbolos.

## <a name="see-also"></a>Confira também
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)