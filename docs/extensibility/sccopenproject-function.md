---
title: Função SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700564"
---
# <a name="sccopenproject-function"></a>Função SccOpenProject
Esta função abre um projeto de controle de origem existente ou cria um novo.

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

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpUser

[dentro, fora] O nome do usuário (para não exceder SCC_USER_SIZE, incluindo o exterminador NULL).

 lpProjName

[em] A seqüência que identifica o nome do projeto.

 lpLocalProjPath

[em] O caminho para a pasta de trabalho para o projeto.

 lpAuxProjPath

[dentro, fora] Uma seqüência auxiliar opcional que identifica o projeto (para não exceder SCC_AUXPATH_SIZE, incluindo o exterminador NULL).

 lpComment

[em] Comente com um novo projeto que está sendo criado.

 lpTextOutProc

[em] Uma função de retorno de chamada opcional para exibir a saída de texto do plug-in do controle de origem.

 dwFlags

[em] Sinaliza se um novo projeto precisa ser criado se o projeto é desconhecido para o plug-in de controle de origem. Valor pode ser `SCC_OP_CREATEIFNEW` uma combinação de e`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Sucesso na abertura do projeto.|
|SCC_E_INITIALIZEFAILED|Projeto não pôde ser inicializado.|
|SCC_E_INVALIDUSER|O usuário não pôde fazer login no sistema de controle de origem.|
|SCC_E_COULDNOTCREATEPROJECT|O projeto não existia antes da chamada;  a `SCC_OPT_CREATEIFNEW` bandeira foi definida, mas o projeto não pôde ser criado.|
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválida.|
|SCC_E_UNKNOWNPROJECT|O projeto é desconhecido para o plug-in de controle de origem, e a `SCC_OPT_CREATEIFNEW` bandeira não foi definida.|
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECFICERROR|Uma falha não específica; o sistema de controle de origem não foi inicializado.|

## <a name="remarks"></a>Comentários
 O IDE pode passar em`lpUser`um nome de usuário ( ), ou pode simplesmente passar em um ponteiro para uma seqüência de string vazia. Se houver um nome de usuário, o plug-in de controle de origem deve usá-lo como padrão. No entanto, se nenhum nome foi passado, ou se o login falhou com o nome dado, o plug-in deve solicitar ao usuário que faça login e retorne o nome válido `lpUser` quando receber um login`.` válido Como o plug-in pode alterar a seqüência de nomes do usuário, o IDE sempre alocará um buffer de tamanho (+1`SCC_USER_LEN`ou SCC_USER_SIZE, o que inclui espaço para o exterminador nulo).

> [!NOTE]
> A primeira ação que o IDE pode ser `SccOpenProject` necessário para executar pode ser uma chamada para a função ou o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por essa razão, ambos têm `lpUser` um parâmetro idêntico.

 `lpAuxProjPath`e`lpProjName` são lidos a partir do arquivo de solução, ou eles são retornados de uma chamada para a `SccGetProjPath` função. Esses parâmetros contêm as strings que o plug-in de controle de origem associa ao projeto e são significativos apenas para o plug-in. Se tais strings não estiverem no arquivo de solução e o usuário não tiver `SccGetProjPath` sido solicitado a navegar (o `lpAuxProjPath` `lpProjName`que retornaria uma seqüência através da função), o IDE passa strings vazias para ambos e , e espera que esses valores sejam atualizados pelo plug-in quando essa função retornar.

 `lpTextOutProc`é um ponteiro para uma função de retorno de chamada fornecida pelo IDE para o plug-in de controle de origem com o propósito de exibir a saída de resultado do comando. Esta função de retorno de chamada é descrita detalhadamente em [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Se o plug-in de controle de origem pretende tirar `SCC_CAP_TEXTOUT` proveito disso, ele deve ter definido a bandeira no [SccInitialize](../extensibility/sccinitialize-function.md). Se essa bandeira não foi definida, ou se o `lpTextOutProc` IDE não suportar esse recurso, será `NULL`.

 O `dwFlags` parâmetro controla o resultado caso o projeto que está sendo aberto não exista atualmente. Consiste em duas `SCC_OP_CREATEIFNEW` bandeiras, `SCC_OP_SILENTOPEN`e . Se o projeto que está sendo aberto já `SCC_OK`existe, a função simplesmente abre o projeto e retorna . Se o projeto não existir `SCC_OP_CREATEIFNEW` e se a bandeira estiver em ação, o plug-in de controle `SCC_OK`de origem pode criar o projeto no sistema de controle de origem, abri-lo e retornar . Se o projeto não existir, `SCC_OP_CREATEIFNEW` e se a bandeira estiver desligada, o plug-in deve então verificar se há a `SCC_OP_SILENTOPEN` bandeira. Se essa bandeira não estiver, o plug-in pode solicitar ao usuário um nome de projeto. Se essa bandeira estiver, o plug-in deve simplesmente retornar `SCC_E_UNKNOWNPROJECT`.

## <a name="calling-order"></a>Ordem de Chamada
 No curso normal dos eventos, o [SccInitialize](../extensibility/sccinitialize-function.md) seria chamado primeiro para abrir uma sessão de controle de código. Uma sessão pode consistir `SccOpenProject`em uma chamada para , seguida por outras chamadas de função de API de controle de fonte, e terminará com uma chamada para o [SccCloseProject](../extensibility/scccloseproject-function.md). Essas sessões podem ser repetidas várias vezes antes que o [SccUninitialize](../extensibility/sccuninitialize-function.md) seja chamado.

 Se o plug-in de `SCC_CAP_REENTRANT` controle `SccInitialize`de origem definir a broca, a seqüência de sessão acima pode ser repetida muitas vezes em paralelo. Diferentes `pvContext` estruturas acompanham as diferentes sessões, nas quais cada uma `pvContext` está associada a um projeto aberto por vez. Com base`pvContext` no parâmetro, o plug-in pode determinar qual projeto é referenciado em qualquer chamada específica. Se o `SCC_CAP_REENTRANT` bit de capacidade não estiver definido, os plug-ins de controle de origem não reentrantes serão limitados em sua capacidade de trabalhar com vários projetos.

> [!NOTE]
> O `SCC_CAP_REENTRANT` bit foi introduzido na versão 1.1 da API Plug-in de controle de origem. Ele não está definido ou é ignorado na versão 1.0, e todos os plug-ins de controle de origem da versão 1.0 são presumidos como não reentrantes.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restrições de comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
