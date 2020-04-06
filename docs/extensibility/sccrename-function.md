---
title: Função SccRename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700423"
---
# <a name="sccrename-function"></a>Função SccRename
Esta função renomeia um arquivo no sistema de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 Lpfilename

[em] O nome do arquivo totalmente qualificado do arquivo sendo renomeado.

 lpNewName

[em] O novo nome totalmente qualificado. Se o caminho do diretório for diferente, então o arquivo passou de um subdiretório para outro.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A operação de renomeação foi concluída com sucesso.|
|SCC_E_PROJNOTOPEN|O projeto não está aberto sob controle de código.|
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a concluir esta operação.|
|SCC_E_COULDNOTCREATEPROJECT|O projeto não pôde ser criado como parte do processo de renomeação.|
|SCC_E_OPNOTPERFORMED|A operação não foi realizada.|
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado ou geral.|

## <a name="remarks"></a>Comentários
 Esta função pode ser usada para renomear um arquivo ou movê-lo de um local para outro no sistema de controle de origem. O plug-in de controle de origem não deve tentar acessar o arquivo em disco. É responsabilidade do IDE renomear o arquivo local.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
