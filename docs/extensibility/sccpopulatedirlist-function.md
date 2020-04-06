---
title: Função SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700563"
---
# <a name="sccpopulatedirlist-function"></a>Função SccPopulateDirList
Esta função determina quais diretórios e arquivos (opcionalmente) são armazenados no controle de origem, dada uma lista de diretórios a serem examinados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 nDirs

[em] Número de caminhos `lpDirPaths` de diretório na matriz.

 lpDirPaths

[em] Matriz de caminhos de diretório a serem examinados.

 pfnPopulate

[em] Função de retorno de chamada para chamar cada caminho `lpDirPaths` de diretório e (opcionalmente) nome de arquivo em (consulte [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obter detalhes).

 pvCallerData

[em] Valor que deve ser passado inalterado para a função de retorno de chamada.

 fOpções

[em] Uma combinação de valores que controlam a forma como os diretórios são processados (consulte a seção "PopulateDirList flags" dos [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para possíveis valores).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Completou com sucesso a operação.|
|SCC_E_UNKNOWNERROR|Ocorreu um erro.|

## <a name="remarks"></a>Comentários
 Apenas os diretórios e (opcionalmente) nomes de arquivos que estão realmente no repositório de controle de origem são passados para a função de retorno de chamada.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Códigos de erro](../extensibility/error-codes.md)
