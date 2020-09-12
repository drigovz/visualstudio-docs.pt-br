---
title: Aplicar configurações em várias conexões de projeto
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 81448760f0417528fd630c4919ce516b32e518c8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034912"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicação de configurações em várias conexões de projeto
Um plug-in de controle do código-fonte criado usando a API de plug-in de controle do código-fonte versão 1,2 pode usar uma operação em lote para executar a mesma operação de controle do código-fonte em vários projetos ou em vários contextos de conexão. Os lotes podem ser usados para eliminar caixas de diálogo redundantes por projeto da experiência do usuário.

 Se um usuário selecionar vários itens que pertencem a mais de uma conexão em um plug-in de controle do código-fonte criado usando a API de plug-in de controle do código-fonte versão 1,1 (por exemplo, dois projetos da Web em diferentes máquinas de compartilhamento de arquivos) e os verificar, o usuário verá a mesma caixa de diálogo repetidamente. Esse cenário ocorre mesmo se o usuário clicar na caixa de seleção **aplicar a todos** na caixa de diálogo, pois o IDE redefine seu estado para cada contexto de conexão.

## <a name="new-capability-flag"></a>Novo sinalizador de funcionalidade
 A `SccBeginBatch` função define o `SCC_CAP_BATCH` sinalizador para indicar que uma operação em lote está em andamento.

## <a name="new-functions"></a>Novas funções
As novas funções a seguir dão suporte à operação em lote:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

A `SCCBeginBatch` função inicia um grupo de operações de controle do código-fonte. A `SccEndBatch` função fecha o grupo. Os grupos não podem ser aninhados.

## <a name="see-also"></a>Confira também
- [O que há de novo na API de plug-in de controle do código-fonte versão 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
