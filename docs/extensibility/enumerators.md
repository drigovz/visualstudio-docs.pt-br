---
title: Enumeradores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37f469ecc0ae097592a128b30a6a6f189d58d94b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863948"
---
# <a name="enumerators"></a>Enumeradores
Esta seção lista os tipos de dados em que a API de plug-in de controle do código-fonte que o plug-in de controle do código-fonte deve saber sobre enumerador.

## <a name="in-this-section"></a>Nesta seção
- [Código de comando](../extensibility/command-code-enumerator.md) enumera as opções para o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funções.

- [Mensagem](../extensibility/message-enumerator.md) enumera os sinalizadores usados para o retorno de chamada, impressão [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Arquivo de código de status](../extensibility/file-status-code-enumerator.md) Contains denominada valores constantes que especificam o estado de um arquivo sob controle do código-fonte.

- [Código de status do diretório](../extensibility/directory-status-code-enumerator.md) Contains denominada valores constantes que especificam o estado de uma pasta sob o controle do código-fonte.

## <a name="related-sections"></a>Seções relacionadas
- [Criar um controle de fonte plug-in](../extensibility/internals/creating-a-source-control-plug-in.md) define o SDK do plug-in de controle de origem e descreve os recursos incluídos.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) solicita ao usuário opções avançadas para o comando fornecido.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) examina a lista de arquivos para seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não coincide com os critérios para o `nCommand`.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens de controle de fonte de plug-in por meio do IDE.

- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md) fornece uma lista completa de todos os elementos na API de plug-in de controle de origem.