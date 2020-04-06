---
title: QUERYCHANGESFUNC | Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701641"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Esta é uma função de retorno de chamada usada pela operação [SccQueryChanges](../extensibility/sccquerychanges-function.md) para enumerar uma coleção de nomes de arquivos e determinar o status de cada arquivo.

 A `SccQueryChanges` função recebe uma lista de arquivos `QUERYCHANGESFUNC` e um ponteiro para o retorno de chamada. O plug-in de controle de origem enumera sobre a lista dada e fornece status (via callback) para cada arquivo da lista.

## <a name="signature"></a>Assinatura

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>parâmetros
 pvCallerData

[em] O `pvCallerData` parâmetro passou pelo chamador (o IDE) para [SccQueryChanges](../extensibility/sccquerychanges-function.md). O plug-in de controle de origem não deve fazer suposições sobre o conteúdo deste valor.

 pChangesData

[em] Ponteiro para uma [estrutura de QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) descrevendo as alterações em um arquivo.

## <a name="return-value"></a>Valor retornado
 O IDE retorna um código de erro apropriado:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Continuar o processamento.|
|SCC_I_OPERATIONCANCELED|Pare o processamento.|
|SCC_E_xxx|Qualquer erro de CCS apropriado deve parar de ser processado.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESEstrutura de dados
 A estrutura passada para cada arquivo parece o seguinte:

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

 dwTamanho Tamanho desta estrutura (em bytes).

 lpFileName O nome original do arquivo para este item.

 dwChangeType Code indicando o status do arquivo:

|Código|Descrição|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Não sei dizer o que mudou.|
|`SCC_CHANGE_UNCHANGED`|Sem alterações de nome para este arquivo.|
|`SCC_CHANGE_DIFFERENT`|Arquivo com uma identidade diferente, mas o mesmo nome existe no banco de dados.|
|`SCC_CHANGE_NONEXISTENT`|O arquivo não existe nem no banco de dados nem localmente.|
|`SCC_CHANGE_DATABASE_DELETED`|Arquivo excluído no banco de dados.|
|`SCC_CHANGE_LOCAL_DELETED`|Arquivo excluído localmente, mas o arquivo ainda existe no banco de dados. Se isso não puder `SCC_CHANGE_DATABASE_ADDED`ser determinado, retorne.|
|`SCC_CHANGE_DATABASE_ADDED`|Arquivo adicionado ao banco de dados, mas não existe localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|O arquivo não existe no banco de dados e é um novo arquivo local.|
|`SCC_CHANGE_RENAMED_TO`|Arquivo renomeado ou movido `lpLatestName`no banco de dados como .|
|`SCC_CHANGE_RENAMED_FROM`|Arquivo renomeado ou movido `lpLatestName`no banco de dados de; se isso é muito caro para rastrear, devolva uma bandeira diferente, como `SCC_CHANGE_DATABASE_ADDED`.|

 lpLatestName O nome do arquivo atual para este item.

## <a name="see-also"></a>Confira também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Códigos do Erro](../extensibility/error-codes.md)
