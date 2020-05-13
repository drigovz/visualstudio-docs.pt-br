---
title: Funções de retorno de chamada implementadas pelo IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739896"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funções de retorno de chamada implementadas pelo IDE
Para tornar a integração com o ambiente de desenvolvimento integrado (IDE) o mais perfeita possível e para fornecer uma experiência unificada ao usuário final, o plug-in de controle de origem pode usar funções de retorno de chamada que são implementadas pelo IDE. O plug-in pode chamar essas funções em momentos apropriados durante uma operação de controle de origem para passar informações ao IDE; o IDE pode, então, exibir essas informações como elementos incorporados em sua ui nativa. O usuário tem uma experiência menos fragmentada neste cenário do que se o plug-in empregasse sua própria ui.

 O arquivo de cabeçalho necessário é *scc.h*. O local padrão é *\Arquivos do programa\VSIP 8.0\EnvSDK\common\inc\\*. Também está na pasta VSIP que tem a amostra de plug-in de controle de origem em *\Arquivos do programa\VSIP 8.0\MSSCCI\\*.

## <a name="in-this-section"></a>Nesta seção
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens do plug-in de controle de origem através do IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Descreve a função de retorno de chamada que é usada pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando o IDE não tem acesso completo a informações que estão disponíveis apenas para o plug-in de controle de origem, como uma lista completa de arquivos sob controle de versão.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Descreve a função de retorno de chamada que é usada pela operação [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Descreve a função de retorno de chamada que é usada pela operação [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Descreve a função de retorno de chamada definida por uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) que permite que o plug-in de controle de origem comunique alterações de nome de volta ao IDE.

## <a name="related-sections"></a>Seções relacionadas
- [SccOpenProject](../extensibility/sccopenproject-function.md) Abre um projeto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina a lista de arquivos para seu status atual. Além disso, `pfnPopulate` usa a função para notificar o chamador `nCommand`quando um arquivo não corresponde aos critérios do .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Examina uma lista de diretórios e arquivos em um projeto ou projetos que estão sob controle de origem. Cada diretório e nome do arquivo encontrado é passado para uma função de retorno de chamada.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Examina as alterações de nome que foram feitas em uma lista de arquivos. Cada nome de arquivo é passado para uma função de retorno de chamada, juntamente com seu status de alteração.

- [SccSetOption](../extensibility/sccsetoption-function.md) Define uma grande variedade de opções. Cada opção `SCC_OPT_xxx` começa com e tem seu próprio conjunto de valores definidos.

- [Plug-ins de controle de fonte](../extensibility/source-control-plug-ins.md) Descreve o conteúdo da seção de referência do SDK plug-in de controle de origem.
