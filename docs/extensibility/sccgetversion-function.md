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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700669"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
Esta função obtém o número da versão da API plug-in de controle de fonte suportada pelo plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 Um `LONG` tipo de dados que contém o número de versão da API plug-in de controle de fonte suportada:

|WORD|Descrição|
|----------|-----------------|
|Hiword|Versão principal|
|Loword|Versão secundária|

## <a name="remarks"></a>Comentários
 Por exemplo, se um plug-in de controle de origem suportar a versão 1.3 da API plug-in de controle de fonte, essa função retornará 0x0103.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
