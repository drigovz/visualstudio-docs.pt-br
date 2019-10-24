---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744968"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Recupera o nome do arquivo para o último erro de carregamento.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 pRetVal

fora Retorna uma cadeia de caracteres que contém o nome do arquivo. PDB associado ao último erro de carregamento.

## <a name="return-value"></a>Valor retornado
 Retorna o último código de erro causado por uma operação de carregamento. Retorna `E_INVALIDARG` se o parâmetro `pRetVal` é `NULL`.

## <a name="example"></a>Exemplo

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Consulte também
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)