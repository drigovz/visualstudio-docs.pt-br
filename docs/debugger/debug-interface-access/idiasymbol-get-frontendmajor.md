---
title: IDiaSymbol::get_frontEndMajor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd15bb798d35ebac1a8f3af7b766ffd9aeea7d8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740630"
---
# <a name="idiasymbolget_frontendmajor"></a>IDiaSymbol::get_frontEndMajor
Recupera o número de versão principal de front-end.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_frontEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o número de versão principal de front-end. Consulte Observações.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="remarks"></a>Comentários
 Normalmente, um compilador é composto por dois elementos principais: o front-end (o analisador), que lida com a análise do código-fonte em um formulário intermediário e um back-end (gerador de código), que converte o formulário intermediário em assembly. Não é incomum que o front-end tenha uma versão diferente do back-end.

 Um número de versão de front-end ou de back-end é composto por três partes: \<major >. \<minor >. \<build >, em que \<major > é o número de versão principal, \<minor > é o número de versão secundária e \<build > é o número de Build. Por exemplo, 13.10.3077.

## <a name="requirements"></a>Requisitos

|Requisito|Descrição|
|-----------------|-----------------|
|Cabeçalho:|dia2.h|
|Versão:|DIA SDK v 7.0|

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)