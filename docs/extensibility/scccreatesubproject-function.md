---
title: Função SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701033"
---
# <a name="scccreatesubproject-function"></a>Função SccCreateSubProject
Essa função cria um subprojeto com o nome dado `lpParentProjPath` sob um projeto pai existente especificado pelo argumento.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpUser

[dentro, fora] O nome de usuário (até SCC_USER_SIZE, incluindo o exterminador NULL).

 lpParentProjPath

[em] Uma seqüência identificando o caminho do projeto pai (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 lpSubProjName

[em] O nome sugerido do subprojeto (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 lpAuxProjPath

[dentro, fora] Corda auxiliar identificando o projeto (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 lpSubProjPath

[dentro, fora] Cadeia de saída identificando o caminho para o subprojeto (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O subprojeto foi criado com sucesso.|
|SCC_E_INITIALIZEFAILED|O projeto pai não pôde ser inicializado.|
|SCC_E_INVALIDUSER|O usuário não pôde fazer login no sistema de controle de origem.|
|SCC_E_COULDNOTCREATEPROJECT|Subprojeto não pode ser criado.|
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválida.|
|SCC_E_UNKNOWNPROJECT|O projeto pai é desconhecido para o plug-in de controle de origem.|
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_CONNECTIONFAILURE|Houve um problema de conexão de conexão de controle de fonte.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Se um subprojeto com o nome já existir, a função pode alterar o nome\<padrão para criar um único, por exemplo, adicionando "_ número>" a ele. O interlocutor deve estar preparado `lpUser` `lpSubProjPath`para `lpAuxProjPath`aceitar mudanças para , e . Os `lpSubProjPath` `lpAuxProjPath` argumentos e argumentos são então usados em uma chamada para o [SccOpenProject](../extensibility/sccopenproject-function.md). Eles não devem ser modificados pelo chamador no retorno. Essas strings fornecem uma maneira para o plug-in de controle de origem rastrear informações que ele precisa associar a um projeto. O IDE do chamador não exibirá esses dois parâmetros no retorno, porque o plug-in pode usar uma seqüência formatada que pode não ser adequada para visualização. A função retorna um código de sucesso ou falha `lpSubProjPath` e, se bem sucedida, preenche a variável com o caminho completo do projeto para o novo projeto.

 Esta função é semelhante ao [SccGetProjPath,](../extensibility/sccgetprojpath-function.md)exceto que ele cria silenciosamente um projeto em vez de solicitar ao usuário que selecione um. Quando `SccCreateSubProject` a função `lpParentProjName` é `lpAuxProjPath` chamada, e não estará vazia e corresponderá a um projeto válido. Essas strings geralmente são recebidas pelo IDE `SccGetProjPath` de uma chamada anterior para a função ou o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 O `lpUser` argumento é o nome de usuário. O IDE passará pelo mesmo nome de usuário `SccGetProjPath`que havia recebido anteriormente , e o plug-in de controle de origem deve usar o nome como padrão. Se o usuário já tiver uma conexão aberta com o plug-in, então o plug-in deve tentar eliminar quaisquer solicitações para garantir que a função funcione silenciosamente. No entanto, se o login falhar, o plug-in deve solicitar ao usuário um login `lpUser`e, quando receber um login válido, passe o nome de volta. Como o plug-in pode alterar essa seqüência, o IDE sempre alocará um buffer de tamanho (SCC_USER_LEN+1 ou SCC_USER_SIZE, o que inclui espaço para o exterminador nulo). Se a seqüência for alterada, a nova seqüência deve ser um nome de login válido (pelo menos tão válido quanto a seqüência antiga).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas para SccCreateSubProject e SccGetParentProjectPath
 A adição de soluções e projetos ao controle de origem foi simplificada no Visual Studio para minimizar o número de vezes que um usuário é solicitado a selecionar locais no sistema de controle de origem. Essas alterações são ativadas pelo Visual Studio se um plug-in `SccCreateSubProject` de `SccGetParentProjectPath`controle de origem suportar ambas as novas funções, e . No entanto, a seguinte entrada de registro pode ser usada para desativar essas alterações e reverter para o comportamento anterior do Visual Studio (Source Control Plug-in API Versão 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se esta entrada de registro não existir ou for definida como dword:000000000, o Visual Studio tentará usar as novas funções e `SccCreateSubProject` `SccGetParentProjectPath`.

 Se a entrada de registro estiver definida como dword:00000001, o Visual Studio não tentará usar essas novas funções, e as operações de adicionar ao trabalho de controle de origem como fizeram em versões anteriores do Visual Studio.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
