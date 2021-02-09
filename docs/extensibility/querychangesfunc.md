---
title: QUERYCHANGESFUNC | Microsoft Docs
description: A função de retorno de chamada QUERYCHANGESFUNC é usada para enumerar uma coleção de nomes de arquivo e determinar o status de cada arquivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8abe32abcb79fada541124f50a750fb4c1edde58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910861"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Essa é uma função de retorno de chamada usada pela operação [SccQueryChanges](../extensibility/sccquerychanges-function.md) para enumerar uma coleção de nomes de arquivo e determinar o status de cada arquivo.

 A `SccQueryChanges` função recebe uma lista de arquivos e um ponteiro para o `QUERYCHANGESFUNC` retorno de chamada. O plug-in de controle do código-fonte enumera sobre a lista fornecida e fornece o status (por meio deste retorno de chamada) para cada arquivo na lista.

## <a name="signature"></a>Assinatura

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parâmetros
 pvCallerData

no O `pvCallerData` parâmetro passado pelo chamador (IDE) para [SccQueryChanges](../extensibility/sccquerychanges-function.md). O plug-in de controle do código-fonte não deve fazer suposições sobre o conteúdo desse valor.

 pChangesData

no Ponteiro para uma estrutura de [estrutura QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) que descreve as alterações em um arquivo.

## <a name="return-value"></a>Valor retornado
 O IDE retorna um código de erro apropriado:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Continuar o processamento.|
|SCC_I_OPERATIONCANCELED|Pare o processamento.|
|SCC_E_xxx|Qualquer erro SCC apropriado deve parar de processar.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Estrutura QUERYCHANGESDATA
 A estrutura passada para cada arquivo é semelhante ao seguinte:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize o tamanho dessa estrutura (em bytes).

 lpFileName o nome do arquivo original para este item.

 dwChangeType o código que indica o status do arquivo:

|Código|Descrição|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Não é possível informar o que mudou.|
|`SCC_CHANGE_UNCHANGED`|Nenhuma alteração de nome para este arquivo.|
|`SCC_CHANGE_DIFFERENT`|Arquivo com uma identidade diferente, mas o mesmo nome existe no banco de dados.|
|`SCC_CHANGE_NONEXISTENT`|O arquivo não existe no banco de dados ou localmente.|
|`SCC_CHANGE_DATABASE_DELETED`|Arquivo excluído no banco de dados.|
|`SCC_CHANGE_LOCAL_DELETED`|Arquivo excluído localmente, mas o arquivo ainda existe no banco de dados. Se isso não puder ser determinado, retorne `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Arquivo adicionado ao banco de dados, mas não existe localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|O arquivo não existe no banco de dados e é um novo arquivo local.|
|`SCC_CHANGE_RENAMED_TO`|Arquivo renomeado ou movido no banco de dados como `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Arquivo renomeado ou movido no banco de dados de `lpLatestName` ; se isso for muito caro para rastrear, retorne um sinalizador diferente, como `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName o nome do arquivo atual para este item.

## <a name="see-also"></a>Consulte também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Códigos de erro](../extensibility/error-codes.md)
