---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702075"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Esta é uma função de retorno de chamada dada à função [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) para atualizar uma coleção de diretórios e (opcionalmente) nomes de arquivos para descobrir quais estão sob controle de origem.

 O `POPDIRLISTFUNC` retorno de chamada deve ser chamado apenas para os diretórios e nomes de arquivos (na lista dada à `SccPopulateDirList` função) que estão realmente sob controle de origem.

## <a name="signature"></a>Assinatura

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>parâmetros
 pvCallerData

[em] Valor do usuário dado a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bPasta

[em] `TRUE` se o `lpDirectoryOrFileName` nome em é um diretório; caso contrário, o nome é um nome de arquivo.

 lpDirectoryOrFileName

[em] Caminho local completo para um diretório ou nome de arquivo que está sob controle de código fonte.

## <a name="return-value"></a>Valor retornado
 O IDE retorna um código de erro apropriado:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Continuar o processamento.|
|SCC_I_OPERATIONCANCELED|Pare o processamento.|
|SCC_E_xxx|Qualquer erro de controle de origem apropriado deve parar de ser processado.|

## <a name="remarks"></a>Comentários
 Se `fOptions` o parâmetro `SccPopulateDirList` da função `SCC_PDL_INCLUDEFILES` contiver o sinalizador, a lista possivelmente conterá nomes de arquivo, bem como nomes de diretórios.

## <a name="see-also"></a>Confira também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Códigos do Erro](../extensibility/error-codes.md)
