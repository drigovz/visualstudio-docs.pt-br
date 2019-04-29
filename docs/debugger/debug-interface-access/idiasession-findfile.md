---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 729b3c323ce2128b18af516ecbffb7b5157f0274
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839362"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera os arquivos de origem pelo nome e compiland.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parâmetros
 `pCompiland`

[in] Uma [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o compiland a ser usado como um contexto para a pesquisa. Definir esse parâmetro como `NULL` para localizar arquivos de origem em todos os compilandos.

 `name`

[in] Especifica o nome do arquivo de origem a ser recuperado. Definir esse parâmetro como `NULL` para todos os arquivos de origem para ser recuperado.

 `option`

[in] Especifica as opções de comparação aplicadas à pesquisa de nome. Os valores do [enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada sozinho ou em combinação.

 `ppResult`

[out] Retorna um [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) recuperado do objeto que contém uma lista dos arquivos de origem.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="example"></a>Exemplo

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Consulte também
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)