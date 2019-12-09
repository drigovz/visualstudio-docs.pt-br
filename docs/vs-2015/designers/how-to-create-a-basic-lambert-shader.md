---
title: Como criar um sombreador Lambert básico | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 038b3e7db7f1e3b79ee3e41b6e256216a39b91bd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664563"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Como criar um sombreador Lambert básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este documento demonstra como usar o Designer de Sombreador e o DGSL (Directed Graph Shader Language) para criar um sombreador de iluminação que implementa o modelo de iluminação de Lambert clássico.

 Este documento demonstra essas atividades:

- Adicionar nós a um grafo de sombreador

- Desconectar nós

- Conectar nós

## <a name="the-lambert-lighting-model"></a>O modelo de iluminação de Lambert
 O modelo de iluminação de Lambert incorpora iluminação ambiente e direcional para sombrear objetos em uma cena 3D. Os componentes do ambiente fornecem um nível básico de iluminação na cena 3D. Os componentes direcionais fornecem iluminação adicional de fontes de luz direcionais (distantes). A iluminação ambiente afeta todas as superfícies da cena igualmente, independentemente da orientação. Para uma determinada superfície, é um produto da cor ambiente da superfície e a cor e a intensidade da luz ambiente na cena. A iluminação direcional afeta cada superfície na cena de maneira diferente, com base na orientação da superfície em relação a direção da fonte de luz. É um produto da cor difusa e a orientação da superfície e a cor, intensidade e direção das fontes de luz. As superfícies que estão voltadas diretamente para a fonte de luz recebem a contribuição máxima e superfícies que estão diretamente voltadas para o lado oposto, não recebem nenhuma contribuição. No modelo de iluminação de Lambert, o componente ambiente e um ou mais componentes direcionais são combinados para determinar a contribuição de cor difusa total para cada ponto no objeto.

 Antes de começar, verifique se a janela **Propriedades** e a **Caixa de Ferramentas** estão sendo exibidas.

#### <a name="to-create-a-lambert-shader"></a>Para criar um sombreador Lambert

1. Crie um sombreador DGSL com o qual trabalhar. Para obter informações sobre como adicionar um sombreador DGSL ao seu projeto, consulte a seção de Introdução em [Designer de Sombreador](../designers/shader-designer.md).

2. Desconectar o nó **Ponto de Cor** do nó **Cor Final**. Escolha o terminal **RGB** do nó **Ponto de Cor** e, em seguida, escolha **Quebrar Links**. Deixe o terminal **Alfa** conectado.

3. Adicione um nó **Lambert** ao grafo. Na **Caixa de Ferramentas**, em **Utilitário**, selecione **Lambert** e mova-o para a superfície de design. O nó Lambert calcula a contribuição de cor difusa total do pixel, com base em parâmetros de iluminação difusa e ambiente.

4. Conecte o nó **Ponto de Cor** ao nó **Lambert**. No modo de **Seleção**, mova o terminal **RGB** do nó **Ponto de Cor** para o terminal **Cor Difusa** do nó **Lambert**. Essa conexão fornece o nó Lambert com a cor difusa interpolada do pixel.

5. Conecte o valor de cor calculado à cor final. Mova o terminal de **Saída** do nó **Lambert** para o terminal **RGB** do nó **Cor Final**.

   A ilustração a seguir mostra o grafo de sombreador concluído e uma visualização do sombreador aplicado a um modelo de bule.

> [!NOTE]
> Para demonstrar melhor o efeito do sombreador nesta ilustração, foi especificada uma cor laranja usando o parâmetro **MaterialDiffuse** do sombreador. Um jogo ou um aplicativo pode usar esse parâmetro para fornecer um valor de cor exclusivo para cada objeto. Para obter informações sobre parâmetros de material, consulte a seção Visualização de Sombreadores em [Designer de Sombreador](../designers/shader-designer.md).

 ![O grafo do sombreador e uma visualização de seu efeito.](../designers/media/digit-lambert-effect-graph.png "Dígito-Lambert-Effect-Graph")

 Determinadas formas podem fornecer melhores visualizações para alguns sombreadores. Para obter mais informações sobre como visualizar sombreadores no Designer de Sombreador, consulte a seção Visualização de Sombreadores em [Designer de Sombreador](../designers/shader-designer.md).

 A ilustração a seguir mostra o sombreador que é descrito neste documento, aplicado a um modelo 3D.

 ![Iluminação Lambert aplicada a um modelo.](../designers/media/digit-lambert-effect-result.png "Lambert de dígitos-efeito-resultado")

 Para obter mais informações sobre como aplicar um sombreador a um modelo 3D, consulte [Como aplicar um sombreador a um modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Consulte também
 [Como aplicar um sombreador a um modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [como: exportar um sombreador](../designers/how-to-export-a-shader.md) [como: criar um Phong sombreador](../designers/how-to-create-a-basic-phong-shader.md) de sombreador de [Designer](../designers/shader-designer.md) [de sombreador](../designers/shader-designer-nodes.md) básico
