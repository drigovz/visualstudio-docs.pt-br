---
title: Aplicação de configurações entre várias conexões de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7d0a13a72613ba72be5a90aa65be991d6ca10b3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657032"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicação de configurações entre várias conexões de projeto
Um plug-in de controle do código-fonte criado usando o código-fonte controle plug-in API versão 1.2, pode usar uma operação em lote para executar a mesma operação de controle do código-fonte entre vários projetos ou vários contextos de conexão. Lotes podem ser usados para eliminar redundantes, caixas de diálogo a experiência do usuário por projeto.

 Se um usuário seleciona vários itens que pertencem a mais de uma conexão em um plug-in de controle do código-fonte criado usando o código-fonte controle plug-in API versão 1.1 (por exemplo, dois projetos para web em máquinas diferentes de compartilhamento de arquivos) e verifica-os, o usuário vê os mesmos caixa de diálogo repetidamente. Esse cenário ocorre mesmo se o usuário clica o **aplicar a todos** caixa na caixa de diálogo de seleção porque o IDE redefine seu estado para cada contexto de conexão.

## <a name="new-capability-flag"></a>Novo sinalizador de recurso
 O `SccBeginBatch` conjuntos de função a `SCC_CAP_BATCH` sinalizador para indicar que uma operação em lote está em andamento.

## <a name="new-functions"></a>Novas funções
Novas funções a seguir dão suporte a operação em lote:

-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

-   [SccEndBatch](../../extensibility/sccendbatch-function.md)

O `SCCBeginBatch` função inicia um grupo de operações de controle do código-fonte. O `SccEndBatch` função fecha o grupo. Os grupos não podem ser aninhados.

## <a name="see-also"></a>Consulte também
- [O que há de novo no controle de fonte de plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)