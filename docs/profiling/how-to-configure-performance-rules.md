---
title: 'Como: Configurar regras de desempenho | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7387cc54e96aec4deea6a65875f693d704d51859
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973960"
---
# <a name="how-to-configure-performance-rules"></a>Como: Configurar regras de desempenho
Os avisos de desempenho das Ferramentas de Criação de Perfil do Visual Studio indicam problemas em um aplicativo analisado que podem causar lentidão na execução do programa. Os avisos também podem indicar que talvez seja necessário alterar os métodos de coleta para coletar dados mais úteis. Os avisos de desempenho são gerados automaticamente em uma sessão de criação de perfil e aparecem na janela **Lista de Erros** quando um arquivo de dados de criação de perfil é aberto no [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Alguns avisos podem não se aplicar aos cenários que você está interessado e alguns avisos podem ser gerados de forma imprecisa. Você pode configurar os avisos de desempenho para mostrar ou ocultar avisos específicos.

### <a name="to-configure-profiler-performance-warnings"></a>Para configurar avisos de desempenho do criador de perfil

1. No menu **Ferramentas**, clique em **Opções**.

2. Expanda **Ferramentas de Desempenho** e, em seguida, clique em **Regras**.

3. Para habilitar ou desabilitar um aviso, marque ou desmarque a caixa de seleção ao lado da **ID** e do nome do aviso.

4. Para especificar o nível de aviso de uma regra, clique na célula **Ação** ao lado da regra e, em seguida, clique em nível de aviso.

    - **Desabilitado** – desabilita a regra (isso é o mesmo que desmarcar a caixa de seleção ao lado da ID da regra).

    - **Aviso** – exibe a regra como um aviso.

    - **Erro** – interrompe a execução da criação de perfil e exibe a regra como um erro.

    - **Informação** – exibe a regra apenas como informação.