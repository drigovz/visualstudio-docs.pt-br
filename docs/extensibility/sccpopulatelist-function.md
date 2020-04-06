---
title: Função SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700527"
---
# <a name="sccpopulatelist-function"></a>Função SccPopulateList
Esta função atualiza uma lista de arquivos para um determinado comando de controle de origem e fornece status de controle de origem em todos os arquivos dados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 nCommand

[em] O comando de controle de origem que `lpFileNames` será aplicado a todos os arquivos da matriz (consulte Código de [comando](../extensibility/command-code-enumerator.md) para uma lista de possíveis comandos).

 nArquivos

[em] Número de arquivos `lpFileNames` na matriz.

 lpFileNames

[em] Uma matriz de nomes de arquivos conhecidos pelo IDE.

 pfnPopulate

[em] A função de retorno de chamada do IDE para chamar para adicionar e remover arquivos (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).

 pvCallerData

[em] Valor que deve ser passado inalterado para a função de retorno de chamada.

 lpStatus

[dentro, fora] Uma matriz para o plug-in de controle de origem para retornar os sinalizadores de status para cada arquivo.

 fOpções

[em] Sinalizadores de comando (consulte a seção "PopulateList flag" dos [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obter detalhes).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Sucesso.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Esta função examina a lista de arquivos para seu status atual. Ele usa `pfnPopulate` a função de retorno de chamada para notificar `nCommand`o chamador quando um arquivo não corresponde aos critérios para o . Por exemplo, se `SCC_COMMAND_CHECKIN` o comando for e um arquivo na lista não for verificado, então o retorno de chamada é usado para informar o chamador. Ocasionalmente, o plug-in de controle de origem pode encontrar outros arquivos que possam fazer parte do comando e adicioná-los. Isso permite, por exemplo, que um usuário do Visual Basic verifique um arquivo .bmp que é usado por seu projeto, mas não aparece no arquivo de projeto Visual Basic. Um usuário escolhe o comando **Obter** no IDE. O IDE exibirá uma lista de todos os arquivos que ele acha que `SccPopulateList` o usuário pode obter, mas antes que a lista seja mostrada, a função é chamada para garantir que a lista a ser exibida esteja atualizada.

## <a name="example"></a>Exemplo
 O IDE constrói uma lista de arquivos que ele acha que o usuário pode obter. Antes de exibir esta lista, ele chama a `SccPopulateList` função, dando ao plug-in de controle de origem a oportunidade de adicionar e excluir arquivos da lista. O plug-in modifica a lista chamando a função de retorno de chamada dada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter mais detalhes).

 O plug-in continua a `pfnPopulate` chamar a função, que adiciona e exclui arquivos, `SccPopulateList` até que seja concluída e, em seguida, retorna da função. O IDE pode então exibir sua lista. A `lpStatus` matriz representa todos os arquivos da lista original passados pelo IDE. O plug-in preenche o status de todos esses arquivos, além de fazer uso da função de retorno de chamada.

> [!NOTE]
> Um plug-in de controle de origem sempre tem a opção de simplesmente retornar imediatamente desta função, deixando a lista como está. Se um plug-in implementar essa função, ele `SCC_CAP_POPULATELIST` pode indicar isso definindo o bitflag de capacidade na primeira chamada para o [SccInitialize](../extensibility/sccinitialize-function.md). Por padrão, o plug-in deve sempre assumir que todos os itens que estão sendo passados são arquivos. No entanto, se `SCC_PL_DIR` o IDE definir a bandeira no `fOptions` parâmetro, todos os itens que estão sendo repassados serão considerados diretórios. O plug-in deve adicionar todos os arquivos que pertencem aos diretórios. O IDE nunca passará em uma mistura de arquivos e diretórios.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
