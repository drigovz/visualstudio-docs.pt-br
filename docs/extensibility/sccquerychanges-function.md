---
title: Função SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700492"
---
# <a name="sccquerychanges-function"></a>Função SccQueryChanges
Esta função enumera uma determinada lista de arquivos, fornecendo informações sobre alterações de nome para cada arquivo através de uma função de retorno de chamada.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 nArquivos

[em] Número de `lpFileNames` arquivos na matriz.

 lpFileNames

[em] Matriz de nomes de arquivos para obter informações sobre.

 Pfncallback

[em] Função de retorno de chamada para chamar cada nome de arquivo da lista (consulte [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obter detalhes).

 pvCallerData

[em] Valor que será passado inalterado para a função de retorno de chamada.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O processo de consulta foi concluído com sucesso.|
|SCC_E_PROJNOTOPEN|O projeto não foi aberto no controle de fontes.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção.|
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado ou geral.|

## <a name="remarks"></a>Comentários
 As alterações que estão sendo consultadas são para o namespace: especificamente, renomeando, adicionando e removendo um arquivo.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Códigos de erro](../extensibility/error-codes.md)
