---
title: 'Idiainjectedsource:: Get_virtualfilename | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ad241532454cf1a086f8e85c4f2e16c29c76b26
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618647"
---
# <a name="idiainjectedsourcegetvirtualfilename"></a>IDiaInjectedSource::get_virtualFilename
Recupera o nome dado ao código-fonte do arquivo; ou seja, o código que foi inserido.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_virtualFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

[out] Retorna o nome dado ao código-fonte de arquivo injetado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)