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
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721479"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
Essa função obtém o número de versão da API de plug-in de controle do código-fonte com suporte pelo plug-in de controle do código-fonte.

## <a name="syntax"></a>Sintaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parâmetros
 nenhuma.

## <a name="return-value"></a>Valor retornado
 Um tipo de dados `LONG` que contém o número de versão da API de plug-in de controle do código-fonte com suporte:

|WORD|Descrição|
|----------|-----------------|
|HIWORD|Versão principal|
|LOWORD|Versão secundária|

## <a name="remarks"></a>Comentários
 Por exemplo, se um plug-in de controle do código-fonte der suporte à versão 1,3 da API de plug-in de controle do código-fonte, essa função retornará 0x0103.

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)