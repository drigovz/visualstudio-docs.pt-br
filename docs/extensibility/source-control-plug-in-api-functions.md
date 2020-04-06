---
title: Funções de API plug-in de controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699917"
---
# <a name="source-control-plug-in-api-functions"></a>Funções de API de plug-in de controle do código-fonte
A API plug-in de controle de origem fornece as seguintes funções, que devem ser implementadas pelo plug-in de controle de origem de acordo com esta API. As assinaturas de cada função e a semântica associada às bandeiras de bit e outros parâmetros são descritas detalhadamente nesta referência.

## <a name="initialization-and-housekeeping-functions"></a>Funções de Inicialização e Limpeza

|Função|Descrição|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Fecha um projeto.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Solicita ao usuário opções avançadas para o comando dado.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Retorna a versão do plug-in de controle de origem.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializa o plug-in de controle de origem. É chamado uma vez para cada instância do plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Abre um projeto.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Uma função genérica usada para definir uma grande variedade de opções. Cada opção `SCC_OPT_xxx` começa com e tem seu próprio conjunto de valores definidos.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Chamado uma vez quando um plug-in de controle de origem precisa ser desligado.|

## <a name="core-source-control-functions"></a>Funções de controle de origem do núcleo

|Função|Descrição|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Adiciona um conjunto de arquivos especificados por nomes de caminho totalmente qualificados ao sistema de controle de origem.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Permite que o usuário navegue por arquivos que já estão no sistema de controle de origem e, em seguida, faça desses arquivos parte do projeto atual.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Verifica uma série de arquivos.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Verifica uma série de arquivos.|
|[SccDiff](../extensibility/sccdiff-function.md)|Mostra as diferenças entre o arquivo do usuário local especificado por um nome de caminho totalmente qualificado e a versão sob controle de origem.|
|[SccGet](../extensibility/sccget-function.md)|Recupera uma cópia somente leitura de um conjunto de arquivos.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Verifica o status dos arquivos que o `SccQueryInfo`chamador perguntou (via ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Faz com que o plug-in de controle de origem inste o usuário para um caminho de projeto significativo para o plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Mostra o histórico de uma matriz de nomes de arquivos locais totalmente qualificados.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Examina a lista de arquivos para seu status atual. Além disso, `pfnPopulate` usa a função para notificar o chamador `nCommand`quando um arquivo não corresponde aos critérios do .|
|[SccProperties](../extensibility/sccproperties-function.md)|Mostra as propriedades de um arquivo totalmente qualificado.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Examina uma lista de arquivos totalmente qualificados para seu status atual.|
|[SccRemove](../extensibility/sccremove-function.md)|Remove o conjunto de arquivos totalmente qualificados do sistema de controle de origem.|
|[SccRename](../extensibility/sccrename-function.md)|Renomeia o arquivo dado para um novo nome no sistema de controle de origem.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Acessa toda a gama de recursos do sistema de controle de origem.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Desfaz um check-out de uma série de arquivos.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funções que suportam capacidade adicional (versão 1.2 da API plug-in de controle de origem)
 Este grupo de funções define a funcionalidade adicional incluída na versão 1.2 da API plug-in de controle de fonte. Eles fornecem acesso a recursos e recursos de controle de origem mais avançados.

|Função|Descrição|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Começa uma operação em lote.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Cria um subprojeto com o nome dado em um projeto pai existente.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Mostra as diferenças entre o diretório do usuário local especificado por um nome de caminho totalmente qualificado e o local do banco de dados de controle de origem.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Examina uma lista de diretórios totalmente qualificados para seu status atual.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termina uma operação em lote.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Retorna o caminho pai do determinado projeto (o projeto deve existir).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Verifica se vários checkouts em um arquivo são permitidos.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Verifica se o plug-in criará o MSSCCPRJ. Arquivos SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funções que suportam capacidade avançada (versão 1.3 da API plug-in de controle de origem)
 Este grupo de funções define a funcionalidade adicional incluída na versão 1.3 da API plug-in de controle de fonte. Eles fornecem acesso a recursos e recursos de controle de origem mais avançados.

|Função|Descrição|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Adiciona uma lista de arquivos do controle de origem ao projeto atual.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera uma lista de arquivos do controle de origem sem uma interface de usuário.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera uma lista de arquivos no controle de origem que são diferentes dos arquivos locais.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera sinalizadores que especificam recursos estendidos suportados pelo plug-in de controle de origem.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera opções específicas do usuário.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Examina uma lista de diretórios e arquivos em um projeto ou projetos que estão sob controle de origem. Cada diretório e nome do arquivo encontrado é passado para uma função de retorno de chamada.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Examina as alterações de nome feitas em uma lista de arquivos. Cada nome de arquivo é passado para uma função de retorno de chamada com seu status de alteração.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: scc.h

 (Fornecido no Ambiente SDK comum inclui pasta, por padrão *[unidade]* \Arquivos do programa\VSIP 8.0\EnvSDK\common\inc; também fornecido na pasta VSIP com a amostra MSSCCI, *[unidade]* \Arquivos do programa\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
- [Criando um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md)
