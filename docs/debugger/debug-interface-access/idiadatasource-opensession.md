---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744926"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Abre uma sessão para consultar símbolos.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parâmetros
ppSession

fora Retorna um objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que representa a sessão aberta.

## <a name="return-value"></a>Valor retornado
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores de retorno para esse método.

|Valor|Descrição|
|-----------|-----------------|
|E_UNEXPECTED|O objeto [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) não foi inicializado anteriormente com uma fonte de símbolos.|
|E_INVALIDARG|Parâmetro `ppSession` inválido.|
|E_OUTOFMEMORY|Memória insuficiente para abrir a sessão.|

## <a name="remarks"></a>Comentários
Esse método abre um objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para uma fonte de dados.

`IDiaSession` objetos implementam consultas na fonte de dados. Uma sessão gerencia um espaço de endereço para cada conjunto de símbolos de depuração. Se o arquivo. exe ou. dll descrito pelos símbolos de fonte de dados estiver ativo em vários intervalos de endereços (por exemplo, porque vários processos foram carregados), uma sessão para cada intervalo de endereços deverá ser usada.

## <a name="example"></a>Exemplo

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Consulte também
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Visão Geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
