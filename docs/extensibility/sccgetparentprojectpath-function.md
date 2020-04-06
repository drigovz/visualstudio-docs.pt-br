---
title: Função SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700711"
---
# <a name="sccgetparentprojectpath-function"></a>Função SccGetParentProjectPath
Esta função determina o caminho do projeto pai de um projeto especificado. Essa função é chamada quando o usuário está adicionando um projeto do Visual Studio para controlar a origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpUser

[dentro, fora] O nome de usuário (até SCC_USER_SIZE, incluindo o exterminador NULL).

 lpProjPath

[em] String identificando o caminho do projeto (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 lpAuxProjPath

[dentro, fora] Corda auxiliar identificando o projeto (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 lpParentProjPath

[dentro, fora] Cadeia de saída identificando o caminho do projeto pai (até SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O caminho do projeto pai foi obtido com sucesso.|
|SCC_E_INITIALIZEFAILED|Projeto não pôde ser inicializado.|
|SCC_E_INVALIDUSER|O usuário não pôde fazer login no plug-in de controle de origem.|
|SCC_E_UNKNOWNPROJECT|O projeto é desconhecido para o plug-in de controle de origem.|
|SCC_E_INVALIDFILEPATH|Caminho de arquivo inválido ou inutilizável.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_PROJSYNTAXERR|Sintaxe de projeto inválida.|
|SCC_E_CONNECTIONFAILURE|Problema de conexão da loja.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Esta função retorna um código de sucesso ou falha `lpParentProjPath` e, se bem-sucedida, preenche a variável com o caminho completo do projeto para o projeto especificado.

 Essa função retorna o caminho do projeto pai de um projeto existente. Para o projeto raiz, a função retorna o caminho do projeto que foi passado (ou seja, o mesmo caminho de projeto raiz). Observe que um caminho de projeto é uma string que é significativa apenas para o plug-in de controle de origem.

 O IDE está preparado para `lpUser` `lpAuxProjPath` aceitar mudanças nos parâmetros também. O IDE persistirá nessas strings e as passará para o [SccOpenProject](../extensibility/sccopenproject-function.md) quando o usuário abrir esse projeto no futuro. Essas strings, portanto, fornecem uma maneira para o plug-in de controle de origem rastrear informações que ele precisa associar a um projeto.

 Esta função é semelhante ao [SccGetProjPath,](../extensibility/sccgetprojpath-function.md)exceto que não solicita ao usuário que selecione um projeto. Ele também nunca cria um novo projeto, mas trabalha apenas com um projeto existente.

 Quando `SccGetParentProjectPath` é `lpProjPath` chamado, e `lpAuxProjPath` não estará vazio e corresponderá a um projeto válido. Essas strings geralmente são recebidas pelo IDE `SccGetProjPath` de uma chamada anterior para a função.

 O `lpUser` argumento é o nome de usuário. O IDE passará pelo mesmo nome de usuário que `SccGetProjPath` havia recebido anteriormente da função, e o plug-in de controle de origem deve usar o nome como padrão. Se o usuário já tiver uma conexão aberta com o plug-in, então o plug-in deve tentar eliminar quaisquer solicitações para garantir que a função funcione silenciosamente. No entanto, se o login falhar, o plug-in deve solicitar ao usuário um login `lpUser`e, quando receber um login válido, passe o nome de volta. Como o plug-in pode alterar essa seqüência, o`SCC_USER_LEN`IDE sempre alocará um buffer de tamanho (+1). Se a seqüência for alterada, a nova seqüência deve ser um nome de login válido (pelo menos tão válido quanto a seqüência antiga).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas para SccCreateSubProject e SccGetParentProjectPath
 A adição de soluções e projetos ao controle de origem foi simplificada no Visual Studio para minimizar o número de vezes que um usuário é solicitado a selecionar locais no sistema de controle de origem. Essas alterações são ativadas pelo Visual Studio se um plug-in de controle de origem `SccGetParentProjectPath` suportar ambas as novas funções, o [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e a função. No entanto, a seguinte entrada de registro pode ser usada para desativar essas alterações e reverter para o comportamento anterior do Visual Studio (Source Control Plug-in API Versão 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Se esta entrada de registro não existir ou for definida como dword:000000000, o Visual Studio tentará usar as novas funções e `SccCreateSubProject``SccGetParentProjectPath`.

 Se a entrada de registro estiver definida como dword:00000001, o Visual Studio não tentará usar essas novas funções, e as operações de adicionar ao trabalho de controle de origem como fizeram em versões anteriores do Visual Studio.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
