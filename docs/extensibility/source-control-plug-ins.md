---
title: Plug-ins de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699900"
---
# <a name="source-control-plug-ins"></a>Plug-ins de controle do código-fonte
A seção de referência SDK plug-in de controle de fonte contém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]a especificação completa da interface que permite que os sistemas de controle de origem sejam integrados com . Ele especifica a sintaxe e a semântica das várias funções e tipos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de dados que o plug-in de controle de origem deve implementar para interagir com o ambiente de desenvolvimento integrado (IDE).

## <a name="in-this-section"></a>Nesta seção
- [Funções de API plug-in de controle de fonte](../extensibility/source-control-plug-in-api-functions.md) Lista funções que devem ser implementadas pelo plug-in de controle de origem para cumprir com a API plug-in de controle de fonte.

- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Descreve funções que o plug-in de controle de origem usa para repassar informações para o IDE enquanto certos comandos são executados.

- [Enumeradores](../extensibility/enumerators.md) Lista os tipos de dados enumeradores na API plug-in de controle de origem que o plug-in de controle de origem deve saber.

- [Sinalizadores de capacidade](../extensibility/capability-flags.md) Descreve as `SCC_CAP_xxx` bandeiras, que indicam as capacidades de um provedor.

- [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) Lista bandeiras que são úteis no contexto de comandos específicos.

- [Códigos de erro](../extensibility/error-codes.md) Lista valores de erro comuns retornados por funções como `SCCTRN`.

- [Strings usadas como chaves para encontrar um plug-in de controle de origem](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Descreve chaves para acessar o registro para encontrar o plug-in de controle de origem.

- [MSSCCPRJ. Arquivo SCC](../extensibility/mssccprj-scc-file.md) Descreve um arquivo do lado do cliente que contém informações opacas ao IDE, mas que é usada pelo plug-in de controle de origem para localizar a solução ou o projeto no controle da versão.

- [Práticas recomendadas para implementar um plug-in de controle de origem](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Fornece uma coleção de lembretes técnicos importantes para lembrar enquanto você está implementando a API plug-in de controle de origem.

- [Restrições aos comprimentos das cordas](../extensibility/restrictions-on-string-lengths.md) Descreve limitações na API plug-in de controle de fonte sobre os comprimentos das strings usadas em várias funções.

- [Glossário](../extensibility/source-control-plug-in-glossary.md) Fornece termos úteis e suas definições para ler a documentação do SDK do Plug-in de controle de fonte.

- [Como: Desativar avisos de compatibilidade para plug-ins de controle de origem](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Descreve como desativar avisos.

## <a name="related-sections"></a>Seções relacionadas
- [Amostra de plug-in de controle de fonte](https://www.microsoft.com/download/details.aspx?id=55984) Fornece uma amostra da funcionalidade de plug-in de controle de origem.

- [Guia de teste para plug-ins de controle de origem](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Descreve procedimentos de teste relacionados a um plug-in de controle de origem.

- [Criando um plug-in de controle de origem](../extensibility/internals/creating-a-source-control-plug-in.md) Discute como criar um plug-in de controle de origem que forneça [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a funcionalidade de controle de origem enquanto você estiver usando a interface do usuário de controle de origem (UI).

- [Referência visual studio SDK](../extensibility/visual-studio-sdk-reference.md) Apresenta uma lista de tópicos de referência.
