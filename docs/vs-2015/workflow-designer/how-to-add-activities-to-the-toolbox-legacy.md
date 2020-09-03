---
title: 'Como: adicionar atividades à caixa de ferramentas (Herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656614"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Como: Adicione atividades a caixa de ferramentas (o legados)
Ao criar uma solução de fluxo de trabalho com o herdado [!INCLUDE[wfd1](../includes/wfd1-md.md)] que visa o [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] , as atividades personalizadas podem ser adicionadas ao projeto de fluxo de trabalho e aos seus designers colocados na **caixa de ferramentas** para facilitar o acesso. Você também pode adicionar atividades diretamente à **caixa de ferramentas** de uma dll (biblioteca de vínculo dinâmico).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para adicionar uma atividade à caixa de ferramentas de uma DLL

1. Clique com o botão direito do mouse na superfície da janela da caixa de ferramentas em **fluxo de trabalho do Windows**e clique em **escolher itens**.

2. Na caixa de diálogo **escolher itens de caixa de ferramentas** , clique na guia **componentes do sistema. atividades** e, em seguida, clique em **procurar** no lado direito inferior da janela.

3. Selecione a DLL do diretório de arquivos que contém a implementação da atividade personalizada a ser adicionada à **caixa de ferramentas**e clique em **abrir**.

4. Clique em **OK** para concluir a adição da atividade à caixa de ferramentas.

## <a name="see-also"></a>Consulte Também
 [Usando as atividades herdadas de fluxo de](../workflow-designer/using-the-legacy-activity-designer.md) [trabalho herdado](../workflow-designer/legacy-workflow-activities.md) do designer de atividades