---
title: Referência (Captura programática) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a462d22df9768d2ffc8b344933e9f5c1f556575a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713588"
---
# <a name="reference-programmatic-capture"></a>Referência (captura programática)
Diagnóstico de gráficos oferece suporte a controle programático sobre seus recursos de captura, por meio da API de captura programática. Você pode usar essa API para ativar/desativar e adicionar mensagens para o diagnóstico de gráficos HUD (Head-Up Display), inicializar e criar arquivos de log de gráficos e capturar informações gráficas.

## <a name="programmatic-capture-apis"></a>APIs de captura programática

### <a name="classes"></a>Classes

|Nome|Descrição|
|----------|-----------------|
|[Classe VsgDbg](vsgdbg-class.md)|Representa a interface por meio do qual o componente no aplicativo de diagnóstico de gráficos é controlado por meio de programação.|

### <a name="preprocessor-symbols"></a>Símbolos de pré-processador

|Nome|Descrição|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Define sua presença se o arquivo de log de gráficos é salvo para o diretório de arquivos temporários do usuário.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Define o nome de arquivo padrão do arquivo de log de gráficos.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Define por sua presença se uma instância padrão do `VsgDbg` classe é fornecida.|

## <a name="related-articles"></a>Artigos relacionados

| Título | Descrição |
| - | - |
| [Capturando informações de gráficos](capturing-graphics-information.md) | Mostra como capturar informações gráficas de seu aplicativo baseado no DirectX para que você possa usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ferramentas de diagnóstico de gráficos para diagnosticar problemas de renderização. |
| [Visão geral](overview-of-visual-studio-graphics-diagnostics.md) | Mostra como o diagnóstico de gráficos podem ajudar você a depurar erros de renderização em aplicativos e jogos do DirectX. |
