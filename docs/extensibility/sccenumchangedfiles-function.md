---
title: Função SccEnumChangedFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700914"
---
# <a name="sccenumchangedfiles-function"></a>Função SccEnumChangedFiles
Dada uma lista de arquivos locais, esta função determina quais arquivos são diferentes das versões correspondentes no banco de dados de controle de código fonte.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 cArquivos

[em] Número de nomes de `lpFileNames` arquivos especificados na matriz. Também especifica o `plIsFileDifferent` tamanho da matriz.

 lpFileNames

[em] Matriz de nomes de arquivos locais para verificar.

 plIsFileDifferent

[dentro, fora] Matriz de valores indicando o status de diferença `cFiles` de cada arquivo (matriz deve ter pelo menos entradas). Não zero significa que o arquivo é diferente.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Operação concluída com sucesso.|
|SCC_UNSPECIFIEDERROR|Erro genérico.|

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
