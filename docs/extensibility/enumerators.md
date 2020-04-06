---
title: Enumeradores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711849"
---
# <a name="enumerators"></a>Enumeradores
Esta seção lista os tipos de dados enumeradores na API plug-in de controle de fonte que o plug-in de controle de origem deve saber.

## <a name="in-this-section"></a>Nesta seção
- [Código de comando](../extensibility/command-code-enumerator.md) Enumera as opções para as funções [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Mensagem](../extensibility/message-enumerator.md) Enumera bandeiras usadas para o retorno de chamada de impressão, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Código de status de arquivo](../extensibility/file-status-code-enumerator.md) Contém valores constantes nomeados que especificam o estado de um arquivo sob controle de origem.

- [Código de status do diretório](../extensibility/directory-status-code-enumerator.md) Contém valores constantes nomeados que especificam o estado de um diretório sob controle de origem.

## <a name="related-sections"></a>Seções relacionadas
- [Criar um plug-in de controle de origem](../extensibility/internals/creating-a-source-control-plug-in.md) Define o SDK plug-in de controle de origem e descreve os recursos incluídos.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Solicita ao usuário opções avançadas para o comando dado.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina a lista de arquivos para seu status atual. Além disso, `pfnPopulate` usa a função para notificar o chamador `nCommand`quando um arquivo não corresponde aos critérios do .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens do plug-in de controle de origem através do IDE.

- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md) Fornece uma lista completa de todos os elementos da API plug-in de controle de fonte.
