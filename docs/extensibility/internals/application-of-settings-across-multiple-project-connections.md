---
title: Aplicação de configurações em várias conexões de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710056"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicação de configurações em várias conexões de projeto
Um plug-in de controle de origem construído usando a API Plug-in de controle de origem Versão 1.2, pode usar uma operação em lote para executar a mesma operação de controle de origem em vários projetos ou vários contextos de conexão. Os lotes podem ser usados para eliminar caixas de diálogo redundantes por projeto da experiência do usuário.

 Se um usuário selecionar vários itens que pertencem a mais de uma conexão em um plug-in de controle de origem construído usando a API Plug-in de controle de origem Versão 1.1 (por exemplo, dois projetos web em diferentes máquinas de compartilhamento de arquivos) e os verificar, o usuário verá a mesma caixa de diálogo repetidamente. Esse cenário ocorre mesmo se o usuário clicar na caixa **Aplicar para Todos** na caixa de diálogo, porque o IDE redefine seu estado para cada contexto de conexão.

## <a name="new-capability-flag"></a>Novo sinalizador de capacidade
 A `SccBeginBatch` função `SCC_CAP_BATCH` define o sinalizador para indicar que uma operação em lote está em andamento.

## <a name="new-functions"></a>Novas funções
As novas funções a seguir suportam a operação em lote:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

A `SCCBeginBatch` função inicia um grupo de operações de controle de origem. A `SccEndBatch` função fecha o grupo. Os grupos podem não estar aninhados.

## <a name="see-also"></a>Confira também
- [O que há de novo na API plug-in de controle de fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
