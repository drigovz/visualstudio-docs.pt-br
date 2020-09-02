---
title: Função SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700669"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
Essa função obtém o número de versão da API de plug-in de controle do código-fonte com suporte pelo plug-in de controle do código-fonte.

## <a name="syntax"></a>Sintaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parâmetros
 Nenhum.

## <a name="return-value"></a>Valor Retornado
 Um `LONG` tipo de dados que contém o número de versão da API de plug-in de controle do código-fonte com suporte:

|WORD|Descrição|
|----------|-----------------|
|HIWORD|Versão principal|
|LOWORD|Versão secundária|

## <a name="remarks"></a>Comentários
 Por exemplo, se um plug-in de controle do código-fonte der suporte à versão 1,3 da API de plug-in de controle do código-fonte, essa função retornará 0x0103.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
