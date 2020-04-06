---
title: Função SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700205"
---
# <a name="sccwillcreatesccfile-function"></a>Função SccWillCreateSccFile
Esta função determina se o plug-in de controle de origem suporta a criação do MSSCCPRJ. Arquivo SCC para cada um dos arquivos dados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 nArquivos

[em] O número de nomes `lpFileNames` de arquivos incluídos na `pbSccFiles` matriz, bem como o comprimento da matriz.

 lpFileNames

[em] Uma matriz de nomes de arquivos totalmente qualificados para verificar (array deve ser alocado pelo chamador).

 pbSccFiles

[dentro, fora] Matriz na qual armazenar os resultados.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Sucesso.|
|SCC_E_INVALIDFILEPATH|Um dos caminhos na matriz é inválido.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Esta função é chamada com uma lista de arquivos para determinar se o plug-in de controle de origem fornece suporte no MSSCCPRJ. Arquivo SCC para cada um dos arquivos dados (para obter mais informações sobre o MSSCCPRJ. Arquivo SCC, ver [MSSCCPRJ. Arquivo SCC](../extensibility/mssccprj-scc-file.md)). Os plug-ins de controle de origem podem declarar se têm a capacidade de criar o MSSCCPRJ. Arquivos SCC declarando `SCC_CAP_SCCFILE` durante a inicialização. O plug-in `TRUE` `FALSE` retorna ou `pbSccFiles` por arquivo na matriz para indicar qual dos arquivos dado tem MSSCCPRJ. Suporte scc. Se o plug-in retornar um código de sucesso da função, os valores na matriz de retorno serão honrados. No fracasso, a matriz é ignorada.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
