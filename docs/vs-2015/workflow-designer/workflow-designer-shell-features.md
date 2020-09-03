---
title: Recursos do Shell de Designer de Fluxo de Trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c59dc8232713d4126b2c37693a1e241735eb163
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606596"
---
# <a name="workflow-designer-shell-features"></a>Recursos de Designer de Fluxo de Trabalho Shell
[!INCLUDE[wfd1](../includes/wfd1-md.md)] é composto por três áreas principais da interface do usuário: a superfície do designer, a barra de navegação estrutural acima dela e o Shell abaixo dela. A barra de rastreamento, posicionado na parte superior da tela, é usada para exibir a lista de ancestrais de atividade da raiz atual. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Como: usar a navegação por trilha](../workflow-designer/how-to-use-breadcrumb-navigation.md). A superfície de designer, posicionado no centro da tela, é usada para compondo fluxos de trabalho. O shell, localizado na parte inferior da tela, contém um número de botões para gerenciar o modo de exibição atual.

## <a name="shell-features"></a>Recursos de Shell
 O shell tem botões no lado direito da barra que você pode usar para ampliar ou do fluxo de trabalho, para caber o conteúdo do fluxo de trabalho o tamanho da tela, e de apresentação ou para ocultar o mapa da revisão. Você também pode ampliar ou fora de um fluxo de trabalho usando os atalhos de teclado CTRL++ e CTRL+-.

## <a name="overview-map"></a>Visão geral de mapa
 O mapa da visão geral exibe uma pequena versão da atividade inteira na raiz atual de rastreamento, incluindo todos seus filhos e todos os seus filhos expandidos. Há um viewport, um retângulo com uma borda laranja, que realça a parte da atividade exibida atualmente dentro do editor. Arraste o retângulo em torno do mapa da visão geral rola o designer de fluxo de trabalho e altera a exibição do editor.

> [!NOTE]
> A interface do usuário de [!INCLUDE[wfd2](../includes/wfd2-md.md)] é virtualizada. Os designers de atividade são processados somente se necessário. Se uma parte do fluxo de trabalho foi desenhada nunca na superfície do designer, essa parte aparece como o branco no mapa da revisão. Rolagem em torno do mapa da visão geral desenha completamente o fluxo de trabalho.

## <a name="copying-or-saving-workflows-as-images"></a>Copiando ou salvando fluxos de trabalho como imagens
 Fluxos de trabalho podem ser copiados no formato de bitmap ou ser salvos no formato de bitmap ou vetorial. Copiar ou salvar uma imagem fornecem uma maneira para exportar um modo de exibição da atividade inteira na raiz atual de rastreamento, incluindo todos seus filhos e todos os seus filhos expandidos a outros programa.

 Para copiar como imagem, clique com o botão direito do mouse em qualquer lugar no designer e selecione **Copiar como imagem**. Para salvar como imagem, clique com o botão direito do mouse em qualquer lugar no designer e selecione **salvar como imagem**. Fluxos de trabalho podem ser salvos no formato de JPG, PNG, GIF, ou XPS. O formato é selecionado na caixa de diálogo **salvar como** na caixa de listagem suspensa **salvar como tipo:** na parte inferior da janela.

## <a name="fonts-and-colors"></a>Fontes e cores
 As fontes usadas em [!INCLUDE[wfd2](../includes/wfd2-md.md)] dentro de [!INCLUDE[vs2010](../includes/vs2010-md.md)] são controladas pela fonte de ambiente. As cores exibidas em [!INCLUDE[wfd2](../includes/wfd2-md.md)] alterações se você estiver usando um esquema de cores de alto contraste para o tema do sistema operacional. Você deve reiniciar [!INCLUDE[vs2010](../includes/vs2010-md.md)] depois de fazer uma alteração na fonte ou cor configurações antes que as alterações tenham efeito em [!INCLUDE[wfd2](../includes/wfd2-md.md)].