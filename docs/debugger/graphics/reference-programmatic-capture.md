---
title: Referência (captura programática) | Microsoft Docs
description: Use a API de captura programática para exercer controle programático sobre os recursos de captura do Diagnóstico de Gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30cf44d6d16da46e9d6f08ffae4971d35136db58
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996104"
---
# <a name="reference-programmatic-capture"></a>Referência (captura programática)
O Diagnóstico de Gráficos dá suporte ao controle programático sobre seus recursos de captura por meio da API de captura programática. Você pode usar essa API para alternar e adicionar mensagens ao HUD de diagnóstico de gráficos (exibição de cabeçalho), inicializar e criar arquivos de log de gráficos e capturar informações de gráficos.

## <a name="programmatic-capture-apis"></a>APIs de captura programática

### <a name="classes"></a>Classes

|Nome|Descrição|
|----------|-----------------|
|[Classe VsgDbg](vsgdbg-class.md)|Representa a interface por meio da qual o componente no aplicativo do diagnóstico de gráficos é controlado programaticamente.|

### <a name="preprocessor-symbols"></a>Símbolos de pré-processador

|Nome|Descrição|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Define por sua presença se o arquivo de log de gráficos é salvo no diretório de arquivos temporários do usuário.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Define o nome de arquivo padrão do arquivo de log de gráficos.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Define por sua presença se uma instância padrão da `VsgDbg` classe é fornecida.|

## <a name="related-articles"></a>Artigos relacionados

| Título | Descrição |
| - | - |
| [Capturando informações de gráficos](capturing-graphics-information.md) | Mostra como capturar informações de gráficos de seu aplicativo baseado em DirectX para que você possa usar as [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para diagnosticar problemas de renderização. |
| [Visão geral](overview-of-visual-studio-graphics-diagnostics.md) | Mostra como Diagnóstico de Gráficos pode ajudá-lo a depurar erros de renderização em jogos e aplicativos do DirectX. |
