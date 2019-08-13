---
title: Animar objetos no XAML Designer
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b396c0428f9810fe41fa70aca7b52fba2dd4f5b
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822202"
---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos no XAML Designer

O Blend para Visual Studio possibilita criar com facilidade animações curtas que movem objetos ou fazem com que eles esmaeçam.

Para criar uma animação, um *storyboard* é necessário. Um storyboard contém uma ou mais *linhas do tempo*. Defina os *quadros chave* em uma linha do tempo para marcar as alterações de propriedade. Depois, ao executar a animação, o Blend para Visual Studio interpola as alterações de propriedade durante o período de tempo designado. O resultado é uma transição suave. É possível animar qualquer propriedade que pertença a um objeto, mesmo propriedades não visuais.

As imagens a seguir mostram o storyboard denominado **Storyboard1**. A linha do tempo contém quadros chave que marcam as posições X e Y de um retângulo. Quando essa animação é executada, o retângulo move de uma posição para outra sem problemas.

![Storyboard para animação no Blend para Visual Studio](../designers/media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Criar uma animação

1. Para criar um storyboard, selecione o botão **Opções de Storyboard** na janela **Objetos e Linha do Tempo** e, em seguida, selecione **Novo**.

   ![Adicionar um storyboard no Blend para Visual Studio](media/new-storyboard.png)

2. Na caixa de diálogo **Criar Recurso de storyboard**, insira um nome para o storyboard.

3. No painel **Ativos** no modo de exibição de Design, adicione um retângulo ao lado esquerdo inferior da página.

   ![Retângulo no painel Ativos do Designer XAML](media/add-rectangle.PNG)

4. Na janela **Objetos e Linha do Tempo**, mova o ponteiro de tempo amarelo para **3** segundos.

   ![Indicador de tempo na linha do tempo](media/timeline-indicator.PNG)

5. No modo de exibição de Design da página, arraste o retângulo para o lado direito da página.

6. Pressione **Reproduzir** para assistir o retângulo se mover do lado esquerdo para o lado direito da página.

Experimente com outras alterações no retângulo em diferentes pontos no tempo. Por exemplo, você pode alterar a cor de preenchimento ou inverter a orientação na janela Propriedades.

## <a name="see-also"></a>Consulte também

- [Criar uma interface do usuário usando o Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)