---
title: Referência (captura programática) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a462d22df9768d2ffc8b344933e9f5c1f556575a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895515"
---
# <a name="reference-programmatic-capture"></a>Referência (captura programática)
O Diagnóstico de Gráficos dá suporte ao controle programático sobre seus recursos de captura por meio da API de captura programática. Você pode usar essa API para alternar e adicionar mensagens ao HUD de diagnóstico de gráficos (exibição de cabeçalho), inicializar e criar arquivos de log de gráficos e capturar informações de gráficos.

## <a name="programmatic-capture-apis"></a>APIs de captura programática

### <a name="classes"></a>Classes

|Name|Descrição|
|----------|-----------------|
|[Classe VsgDbg](vsgdbg-class.md)|Representa a interface por meio da qual o componente no aplicativo do diagnóstico de gráficos é controlado programaticamente.|

### <a name="preprocessor-symbols"></a>Símbolos de pré-processador

|Name|Descrição|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Define por sua presença se o arquivo de log de gráficos é salvo no diretório de arquivos temporários do usuário.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Define o nome de arquivo padrão do arquivo de log de gráficos.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Define por sua presença se uma instância padrão da `VsgDbg` classe é fornecida.|

## <a name="related-articles"></a>Artigos relacionados

| Título | Descrição |
| - | - |
| [Capturando informações de gráficos](capturing-graphics-information.md) | Mostra como capturar informações de gráficos de seu aplicativo baseado em DirectX para que você possa usar as [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para diagnosticar problemas de renderização. |
| [Visão geral](overview-of-visual-studio-graphics-diagnostics.md) | Mostra como Diagnóstico de Gráficos pode ajudá-lo a depurar erros de renderização em jogos e aplicativos do DirectX. |
