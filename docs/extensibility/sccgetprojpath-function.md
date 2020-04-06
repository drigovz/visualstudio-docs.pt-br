---
title: Função SccGetProjPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700698"
---
# <a name="sccgetprojpath-function"></a>Função SccGetProjPath
Essa função solicita ao usuário um caminho de projeto, que é uma string que é significativa apenas para o plug-in de controle de origem. É chamado quando o usuário é:

- Crie um novo projeto

- Adicionando um projeto existente ao controle de versão

- Tentando encontrar um projeto de controle de versão existente

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpUser

[dentro, fora] O nome do usuário (para não exceder SCC_USER_SIZE, incluindo o exterminador NULL)

 lpProjName

[dentro, fora] O nome do projeto IDE, espaço de trabalho do projeto ou makefile (para não exceder SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 lpLocalPath

[dentro, fora] O projeto está funcionando. Se `bAllowChangePath` `TRUE`for, o plug-in de controle de origem pode modificar esta seqüência (para não exceder _MAX_PATH, incluindo o exterminador nulo).

 lpAuxProjPath

[dentro, fora] Um buffer para o caminho do projeto retornado (para não exceder SCC_PRJPATH_SIZE, incluindo o exterminador NULL).

 bAllowChangePath

[em] Se isso `TRUE`for, o plug-in de controle `lpLocalPath` de origem pode solicitar e modificar a seqüência de string.

 pbNovo

[dentro, fora] O valor que está chegando indica a criação de um novo projeto. Valor retornado indica sucesso na criação de um projeto:

|Entrada|Interpretação|
|--------------|--------------------|
|TRUE|O usuário pode criar um novo projeto.|
|FALSE|O usuário pode não criar um novo projeto.|

|Saída|Interpretação|
|--------------|--------------------|
|TRUE|Um novo projeto foi criado.|
|FALSE|Um projeto já existente foi selecionado.|

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O projeto foi criado ou recuperado com sucesso.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção.|
|SCC_E_CONNECTIONFAILURE|Houve um problema tentando se conectar ao sistema de controle de origem.|
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|

## <a name="remarks"></a>Comentários
 O objetivo desta função é que o `lpProjName` IDE adquira os parâmetros e `lpAuxProjPath`. Depois que o plug-in de controle de origem solicita ao usuário essas informações, ele passa essas duas strings de volta para o IDE. O IDE persiste essas strings em seu arquivo de solução e as passa para o [SccOpenProject](../extensibility/sccopenproject-function.md) sempre que o usuário abre este projeto. Essas strings permitem que o plug-in rastreie as informações associadas a um projeto.

 Quando a função é `lpAuxProjPath` chamada pela primeira vez, é definido como uma seqüência vazia. `lProjName`também pode estar vazio, ou pode conter o nome do projeto IDE, que o plug-in de controle de origem pode usar ou ignorar. Quando a função retorna com sucesso, o plug-in retorna as duas strings correspondentes. O IDE não faz suposições sobre essas strings, não as usará e não permitirá que o usuário as modifique. Se o usuário quiser alterar as configurações, `SccGetProjPath` o IDE ligará novamente, passando os mesmos valores que havia recebido na época anterior. Isso dá ao plug-in controle completo sobre essas duas cordas.

 Para `lpUser`, o IDE pode passar em um nome de usuário, ou ele pode simplesmente passar em um ponteiro para uma seqüência de string vazia. Se houver um nome de usuário, o plug-in de controle de origem deve usá-lo como padrão. No entanto, se nenhum nome foi passado ou se o login falhou com o nome dado, o plug-in deve solicitar ao usuário um login e passar o nome de volta `lpUser` quando ele receber um login válido. Como o plug-in pode alterar essa seqüência, o`SCC_USER_LEN`IDE sempre alocará um buffer de tamanho (+1).

> [!NOTE]
> A primeira ação que o IDE realiza `SccOpenProject` pode ser `SccGetProjPath` uma chamada para a função ou para a função. Assim, ambos têm um `lpUser` parâmetro idêntico, que permite que o plug-in de controle de origem faça login em qualquer momento. Mesmo que o retorno da função indique uma falha, o plug-in deve preencher essa seqüência com um nome de login válido.

 `lpLocalPath`é o diretório onde o usuário mantém o projeto. Pode ser uma corda vazia. Se não houver um diretório definido no momento (como no caso de um usuário tentar `bAllowChangePath` baixar `TRUE`um projeto do sistema de controle de origem) e se houver, `lpLocalPath`o plug-in de controle de origem pode solicitar ao usuário a entrada ou usar algum outro método para colocar sua própria string em . Se `bAllowChangePath` `FALSE`for, o plug-in não deve alterar a seqüência, porque o usuário já está trabalhando no diretório especificado.

 Se o usuário criar um novo projeto a ser colocado sob controle de origem, o plug-in de controle de origem pode não realmente criá-lo no sistema de controle de origem no momento `SccGetProjPath` em que é chamado. Em vez disso, ele repassa a `pbNew`seqüência juntamente com um valor não zero para, indicando que o projeto será criado no sistema de controle de origem.

 Por exemplo, se um usuário no assistente **do Novo Projeto** no Visual Studio adicionar seu projeto ao controle de origem, o Visual Studio chama essa função e o plug-in determina se está tudo bem criar um novo projeto no sistema de controle de origem para conter o projeto Visual Studio. Se o usuário clicar **em Cancelar** antes de concluir o assistente, o projeto nunca será criado. Se o usuário clicar em `SccOpenProject` **OK,** o Visual Studio ligar, passar `SCC_OPT_CREATEIFNEW`e o projeto controlado de origem for criado nesse momento.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
