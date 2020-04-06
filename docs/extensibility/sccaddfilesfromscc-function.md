---
title: Função SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701282"
---
# <a name="sccaddfilesfromscc-function"></a>Função SccAddFilesFromSCC
Esta função adiciona uma lista de arquivos do controle de origem ao projeto atualmente aberto.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpUser

[dentro, fora] O nome de usuário (até SCC_USER_SIZE, incluindo o exterminador nulo).

 lpAuxProjPath

[dentro, fora] Seqüência auxiliar identificando o `SCC_PRJPATH_`projeto (até TAMANHO, incluindo o exterminador nulo).

 cArquivos

[em] Número de arquivos `lpFilePaths`dados por .

 lpFilePaths

[dentro, fora] Matriz de nomes de arquivos para adicionar ao projeto atual.

 lpDestino

[em] O caminho de destino onde os arquivos devem ser escritos.

 lpComment

[em] O comentário a ser aplicado a cada um dos arquivos a serem adicionados.

 pbResultados

[dentro, fora] Matriz de sinalizadores definidos para indicar sucesso (não zero ou TRUE) ou falha (zero ou `cFiles` FALSO) para cada arquivo (o tamanho da matriz deve ser pelo menos longo).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|O projeto não está aberto.|
|SCC_E_OPNOTPERFORMED|Conexão não é para o mesmo projeto especificado por`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a atualizar o banco de dados.|
|SCC_E_NONSPECIFICERROR|Erro desconhecido.|
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
