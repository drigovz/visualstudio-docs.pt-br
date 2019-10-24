---
title: Função SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721048"
---
# <a name="sccopenproject-function"></a>Função SccOpenProject
Essa função abre um projeto de controle do código-fonte existente ou cria um novo.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parâmetros
 pvContext

no A estrutura de contexto do plug-in de controle do código-fonte.

 hWnd

no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.

 lpUser

[entrada, saída] O nome do usuário (não deve exceder SCC_USER_SIZE, incluindo o terminador nulo).

 lpProjName

no A cadeia de caracteres que identifica o nome do projeto.

 lpLocalProjPath

no O caminho para a pasta de trabalho do projeto.

 lpAuxProjPath

[entrada, saída] Uma cadeia de caracteres auxiliar opcional que identifica o projeto (sem exceder o SCC_AUXPATH_SIZE, incluindo o terminador nulo).

 lpComment

no Comente para um novo projeto que está sendo criado.

 lpTextOutProc

no Uma função de retorno de chamada opcional para exibir a saída de texto do plug-in de controle do código-fonte.

 dwFlags

no Sinaliza se um novo projeto precisa ser criado se o projeto for desconhecido para o plug-in de controle do código-fonte. O valor pode ser uma combinação de `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Êxito ao abrir o projeto.|
|SCC_E_INITIALIZEFAILED|Não foi possível inicializar o projeto.|
|SCC_E_INVALIDUSER|O usuário não pôde fazer logon no sistema de controle do código-fonte.|
|SCC_E_COULDNOTCREATEPROJECT|O projeto não existia antes da chamada;  o sinalizador de `SCC_OPT_CREATEIFNEW` foi definido, mas não foi possível criar o projeto.|
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválida.|
|SCC_E_UNKNOWNPROJECT|O projeto é desconhecido para o plug-in de controle do código-fonte e o sinalizador `SCC_OPT_CREATEIFNEW` não foi definido.|
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção. Uma nova tentativa é recomendada.|
|SCC_E_NONSPECFICERROR|Uma falha não específica; o sistema de controle do código-fonte não foi inicializado.|

## <a name="remarks"></a>Comentários
 O IDE pode passar um nome de usuário (`lpUser`) ou pode simplesmente passar um ponteiro para uma cadeia de caracteres vazia. Se houver um nome de usuário, o plug-in de controle do código-fonte deverá usá-lo como padrão. No entanto, se nenhum nome foi passado ou se o logon falhou com o nome fornecido, o plug-in deverá solicitar que o usuário faça logon e retornará o nome válido em `lpUser` quando receber um logon válido `.` porque o plug-in pode alterar a cadeia de caracteres de nome de usuário , o IDE sempre alocará um buffer de tamanho (`SCC_USER_LEN` + 1 ou SCC_USER_SIZE, que inclui o espaço para o terminador nulo).

> [!NOTE]
> A primeira ação que o IDE pode precisar executar pode ser uma chamada para a função `SccOpenProject` ou [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por esse motivo, ambos têm um parâmetro de `lpUser` idêntico.

 `lpAuxProjPath` e `lpProjName` são lidos a partir do arquivo de solução ou são retornados de uma chamada para a função `SccGetProjPath`. Esses parâmetros contêm as cadeias de caracteres que o plug-in de controle do código-fonte associa ao projeto e são significativos apenas para o plug-in. Se nenhuma cadeia de caracteres estiver no arquivo de solução e o usuário não tiver sido solicitado a procurar (que retornaria uma cadeia de caracteres por meio da função `SccGetProjPath`), o IDE passa cadeias de caracteres vazias para `lpAuxProjPath` e `lpProjName` e espera que esses valores sejam atualizados pelo plug-in quando o a função é retornada.

 `lpTextOutProc` é um ponteiro para uma função de retorno de chamada fornecida pelo IDE para o plug-in de controle do código-fonte com a finalidade de exibir a saída do resultado do comando. Essa função de retorno de chamada é descrita em detalhes em [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Se o plug-in de controle do código-fonte pretende tirar proveito disso, ele deve ter definido o sinalizador `SCC_CAP_TEXTOUT` no [SccInitialize](../extensibility/sccinitialize-function.md). Se esse sinalizador não tiver sido definido ou se o IDE não oferecer suporte a esse recurso, `lpTextOutProc` será `NULL`.

 O parâmetro `dwFlags` controla o resultado no caso em que o projeto que está sendo aberto não exista atualmente. Ele consiste em dois bitflags, `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN`. Se o projeto que está sendo aberto já existir, a função simplesmente abrirá o projeto e retornará `SCC_OK`. Se o projeto não existir e se o sinalizador de `SCC_OP_CREATEIFNEW` estiver ativado, o plug-in de controle do código-fonte poderá criar o projeto no sistema de controle do código-fonte, abri-lo e retornar `SCC_OK`. Se o projeto não existir e se o sinalizador de `SCC_OP_CREATEIFNEW` estiver desativado, o plug-in deverá verificar o sinalizador de `SCC_OP_SILENTOPEN`. Se esse sinalizador não estiver ativado, o plug-in poderá solicitar ao usuário um nome de projeto. Se esse sinalizador estiver ativado, o plug-in deverá simplesmente retornar `SCC_E_UNKNOWNPROJECT`.

## <a name="calling-order"></a>Ordem de chamada
 No curso normal de eventos, o [SccInitialize](../extensibility/sccinitialize-function.md) seria chamado primeiro para abrir uma sessão de controle do código-fonte. Uma sessão pode consistir em uma chamada para `SccOpenProject`, seguida por outras chamadas de função da API de plug-in de controle do código-fonte e será encerrada com uma chamada para o [SccCloseProject](../extensibility/scccloseproject-function.md). Essas sessões podem ser repetidas várias vezes antes de o [SccUninitialize](../extensibility/sccuninitialize-function.md) ser chamado.

 Se o plug-in de controle do código-fonte definir o `SCC_CAP_REENTRANT` bit em `SccInitialize`, a sequência de sessão acima poderá ser repetida muitas vezes em paralelo. Estruturas de `pvContext` diferentes controlam as diferentes sessões, nas quais cada `pvContext` está associada a um projeto aberto por vez. Com base no parâmetro `pvContext`, o plug-in pode determinar qual projeto é referenciado em qualquer chamada específica. Se o bit de funcionalidade `SCC_CAP_REENTRANT` não estiver definido, os plug-ins de controle do código-fonte do nonreentrant serão limitados em sua capacidade de trabalhar com vários projetos.

> [!NOTE]
> O bit de `SCC_CAP_REENTRANT` foi introduzido na versão 1,1 da API de plug-in de controle do código-fonte. Ele não está definido ou é ignorado na versão 1,0 e todos os plug-ins de controle do código-fonte da versão 1,0 são considerados nonreentrant.

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restrições aos comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)