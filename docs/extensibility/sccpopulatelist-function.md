---
title: Função SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720867"
---
# <a name="sccpopulatelist-function"></a>Função SccPopulateList
Essa função atualiza uma lista de arquivos para um comando de controle do código-fonte específico e fornece o status do controle do código-fonte em todos os arquivos fornecidos.

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

#### <a name="parameters"></a>Parâmetros
 pvContext

no A estrutura de contexto do plug-in de controle do código-fonte.

 Ncomando

no O comando de controle do código-fonte que será aplicado a todos os arquivos na matriz de `lpFileNames` (consulte o [código de comando](../extensibility/command-code-enumerator.md) para obter uma lista de comandos possíveis).

 nFiles

no Número de arquivos na matriz de `lpFileNames`.

 lpFileNames

no Uma matriz de nomes de arquivo conhecida pelo IDE.

 pfnPopulate

no A função de retorno de chamada do IDE para chamar adicionar e remover arquivos (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).

 pvCallerData

no Valor que deve ser passado inalterado para a função de retorno de chamada.

 lpStatus

[entrada, saída] Uma matriz para o plug-in de controle do código-fonte para retornar os sinalizadores de status de cada arquivo.

 fOptions

no Sinalizadores de comando (consulte a seção "sinalizador de populalist" de [Bitflags usada por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obter detalhes).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Êxito.|
|SCC_E_NONSPECIFICERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 Essa função examina a lista de arquivos para seu status atual. Ele usa a função de retorno de chamada `pfnPopulate` para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`. Por exemplo, se o comando for `SCC_COMMAND_CHECKIN` e um arquivo na lista não for submetido a check-out, o retorno de chamada será usado para informar o chamador. Ocasionalmente, o plug-in de controle do código-fonte pode encontrar outros arquivos que podem fazer parte do comando e adicioná-los. Isso permite, por exemplo, um usuário Visual Basic para fazer check-out de um arquivo. bmp que é usado pelo seu projeto, mas não aparece no arquivo de projeto Visual Basic. Um usuário escolhe o comando **Get** no IDE. O IDE exibirá uma lista de todos os arquivos que acha que o usuário pode obter, mas antes de a lista ser mostrada, a função `SccPopulateList` é chamada para verificar se a lista a ser exibida está atualizada.

## <a name="example"></a>Exemplo
 O IDE cria uma lista de arquivos que ele acha que o usuário pode obter. Antes de exibir essa lista, ela chama a função `SccPopulateList`, dando ao plug-in de controle do código-fonte a oportunidade de adicionar e excluir arquivos da lista. O plug-in modifica a lista chamando a função de retorno de chamada fornecida (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter mais detalhes).

 O plug-in continua a chamar a função `pfnPopulate`, que adiciona e exclui arquivos, até que ele seja concluído e, em seguida, retorne da função `SccPopulateList`. O IDE pode exibir sua lista. A matriz de `lpStatus` representa todos os arquivos na lista original passados pelo IDE. O plug-in preenche o status de todos esses arquivos, além de fazer uso da função de retorno de chamada.

> [!NOTE]
> Um plug-in de controle do código-fonte sempre tem a opção de simplesmente retornar imediatamente dessa função, deixando a lista como está. Se um plug-in implementar essa função, isso poderá indicar isso definindo o recurso de `SCC_CAP_POPULATELIST` bitflag na primeira chamada para o [SccInitialize](../extensibility/sccinitialize-function.md). Por padrão, o plug-in sempre deve assumir que todos os itens que estão sendo passados são arquivos. No entanto, se o IDE definir o sinalizador `SCC_PL_DIR` no parâmetro `fOptions`, todos os itens que estão sendo passados serão considerados diretórios. O plug-in deve adicionar todos os arquivos que pertencem aos diretórios. O IDE nunca passará em uma mistura de arquivos e diretórios.

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
- [Código de comando](../extensibility/command-code-enumerator.md)