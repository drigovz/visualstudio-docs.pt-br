---
title: Restrições em comprimentos de cadeia de caracteres | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab797f76ec6f6118fe4f86a410dbfcfe1e61aa04
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334184"
---
# <a name="restrictions-on-string-lengths"></a>Restrições em comprimentos de cadeia de caracteres
A API de plug-in de controle do código-fonte limita os comprimentos das cadeias de caracteres usadas em várias funções.

## <a name="string-length-values"></a>Valores de comprimento de cadeia de caracteres

|Constante|Valor|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Tamanho não inclui a terminação `null`. Outras constantes com um sufixo tamanho"em vez de"_LEN"incluir espaço para a terminação `null`.

|Constante|Valor|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Consulte também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)