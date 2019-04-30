---
title: Restrições em comprimentos de cadeia de caracteres | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ade5e9ac188cd6c1b721ed276e0c4e2aff71f32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434745"
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