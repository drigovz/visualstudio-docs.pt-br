---
title: Função SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ad37e30cfcf913477044e67baaa65dc3af5b9d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353630"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
Essa função obtém o número de versão de API de plug-in de controle de origem compatível com o plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parâmetros
 nenhuma.

## <a name="return-value"></a>Valor de retorno
 Um `LONG` tipo de dados que contém o número de versão de API de plug-in de controle de origem com suporte:

|WORD|Descrição|
|----------|-----------------|
|HIWORD|Versão principal|
|LOWORD|Versão secundária|

## <a name="remarks"></a>Comentários
 Por exemplo, se um plug-in de controle de origem dá suporte à versão 1.3 da API de plug-in de controle de origem, essa função retornará 0x0103.

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)