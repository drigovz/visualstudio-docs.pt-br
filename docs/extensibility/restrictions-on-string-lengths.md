---
title: Restrições em comprimentos de cadeia de caracteres | Microsoft Docs
description: Saiba mais sobre os limites de comprimentos das cadeias de caracteres usados por várias funções impostas pela API de plug-in de controle do código-fonte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd1720553592b0cfbac8be412002ef1b39bfd5bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836950"
---
# <a name="restrictions-on-string-lengths"></a>Restrições em comprimentos de cadeia de caracteres
A API de plug-in de controle do código-fonte limita os comprimentos das cadeias de caracteres usadas em várias funções.

## <a name="string-length-values"></a>Valores de comprimento da cadeia de caracteres

|Constante|Valor|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> O comprimento não inclui o encerramento `null` . Outras constantes com um sufixo "_SIZE" em vez de "_LEN" incluem espaço para o encerramento `null` .

|Constante|Valor|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
