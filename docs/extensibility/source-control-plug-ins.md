---
title: Plug-ins de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01e7a0ca8a509d430a0794a2cedb4b2e9d869585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331822"
---
# <a name="source-control-plug-ins"></a>Plug-ins de controle do código-fonte
A seção de referência do SDK de plug-in de controle do código-fonte contém a especificação de interface completa que permite que os sistemas de controle de origem sejam integrados [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Especifica a sintaxe e semântica das várias funções e tipos de dados que o plug-in de controle de origem deve implementar a interface com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE).

## <a name="in-this-section"></a>Nesta seção
- [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md) lista as funções que devem ser implementadas pelo plug-in de controle do código-fonte para estar em conformidade com a API de plug-in de controle do código-fonte.

- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md) descreve as funções que o plug-in de controle de origem usa para passar informações de volta para o IDE enquanto certos comandos são executados.

- [Enumeradores](../extensibility/enumerators.md) lista os tipos de dados de enumerador na API de plug-in de controle de origem que o plug-in de controle do código-fonte deve conhecer.

- [Sinalizadores de recurso](../extensibility/capability-flags.md) descreve o `SCC_CAP_xxx` sinalizadores, que são indicam os recursos de um provedor.

- [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) lista os sinalizadores que são úteis no contexto de comandos específicos.

- [Códigos de erro](../extensibility/error-codes.md) lista os valores de erro comuns retornados por funções como `SCCTRN`.

- [Cadeias de caracteres usada como chaves para localizar um plug-in de controle do código-fonte](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) descreve as chaves para acessar o registro para localizar o controle de fonte de plug-in.

- [MSSCCPRJ. Arquivos SCC](../extensibility/mssccprj-scc-file.md) descreve um arquivo do lado do cliente que contém informações opacas para o IDE, mas que é usado pelo plug-in de controle da fonte para localizar a solução ou projeto no controle de versão.

- [Práticas recomendadas para implementar um plug-in de controle do código-fonte](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) fornece uma coleção de lembretes técnicas importantes lembrar-se enquanto você estiver implementando a API de plug-in de controle do código-fonte.

- [Restrições em comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md) descreve as limitações na API de plug-in de controle do código-fonte em comprimentos de cadeias de caracteres usadas em várias funções.

- [Glossário](../extensibility/source-control-plug-in-glossary.md) fornece termos úteis e suas definições para ler a documentação do SDK de plug-in de controle do código-fonte.

- [Como: Ativar desativar avisos de compatibilidade para Plug-ins de controle de origem](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) descreve como desabilitar avisos.

## <a name="related-sections"></a>Seções relacionadas
- [Exemplo de plug-in de controle de origem](https://www.microsoft.com/download/details.aspx?id=55984) fornece um exemplo da funcionalidade de plug-in de controle do código-fonte.

- [Guia de teste para Plug-ins de controle de origem](../extensibility/internals/test-guide-for-source-control-plug-ins.md) descreve procedimentos de teste relacionados a um plug-in de controle de origem.

- [Criando um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md) discute como criar um plug-in de controle de fonte que fornece funcionalidade de controle do código-fonte enquanto você estiver usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface de usuário de controle do código-fonte (UI).

- [Referência de SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md) apresenta uma lista de tópicos de referência.