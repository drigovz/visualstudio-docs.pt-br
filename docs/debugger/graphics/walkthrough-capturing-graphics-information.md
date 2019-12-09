---
title: 'Walkthrough: capturando informações de gráficos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aab86d42cd158ad64ebb16497b8d2d9f5a7002df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734733"
---
# <a name="walkthrough-capturing-graphics-information"></a>Passo a passo: capturando informações de gráficos
Este tutorial demonstra como usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnóstico de Gráficos para capturar manualmente informações de gráficos de um aplicativo do Direct3D.

 Este tutorial ilustra essas tarefas:

- Vinculando Diagnóstico de Gráficos ao seu aplicativo

- Capturando informações de gráficos

## <a name="capturing-graphics-information"></a>Capturando informações de gráficos
 Para usar as ferramentas de diagnóstico de gráficos, primeiro, você precisa capturar as informações gráficas nas quais ele confia. Para habilitar a captura, use o comando **Iniciar diagnóstico** para conectar diagnóstico de gráficos ao seu aplicativo quando ele for iniciado.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Para habilitar a captura de informações gráficas após o carregamento de um projeto ou solução

1. Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregue um arquivo de projeto ou de solução para o aplicativo do qual você deseja capturar informações sobre elementos gráficos.

2. Na barra de ferramentas Diagnóstico de Gráficos, escolha **Iniciar diagnóstico**.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Para habilitar a captura de informações gráficas sem carregar um projeto ou uma solução

1. Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**. A caixa de diálogo **Abrir projeto** é exibida.

2. Em vez de um arquivo de projeto ou de solução, especifique o arquivo executável do aplicativo do qual você deseja capturar informações de elementos gráficos e, em seguida, escolha **abrir**.

3. Na barra de menus, escolha **Depurar**, **Gráficos**, **Iniciar Diagnóstico**.

   Depois que você iniciar o aplicativo e ele estiver renderizando quadros, você poderá capturar informações de gráficos.

#### <a name="to-capture-graphics-information"></a>Para capturar informações gráficas

- Na barra de ferramentas Diagnóstico de Gráficos, escolha o botão **capturar** . ![Ícone do botão de captura de gráficos](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   \- ou -

   Com o aplicativo em foco, pressione a **tela de impressão**.

  Cada vez que você captura informações sobre um quadro, Diagnóstico de Gráficos registra os eventos do Direct3D e o estado associado e adiciona esses dados a um log de gráficos. Um novo log de gráficos é criado para cada sessão de Diagnóstico de Gráficos. Para obter informações sobre logs de gráficos, consulte [visão geral](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="next-steps"></a>Próximas etapas
 Este tutorial demonstrou como capturar informações gráficas manualmente. Como próxima etapa, considere esta opção:

- Saiba como analisar as informações de gráficos capturadas usando as ferramentas de Diagnóstico de Gráficos. Consulte [visão geral](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Consulte também
- [Capturando informações de gráficos](capturing-graphics-information.md)