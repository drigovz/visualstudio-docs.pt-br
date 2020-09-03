---
title: Como criar um sombreador de cor básico | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90f27e2359954e56a5b3d86bfc31883d4f29c44d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664583"
---
# <a name="how-to-create-a-basic-color-shader"></a>Como criar um sombreador de cor básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este documento demonstra como usar o Designer de Sombreador e a DGSL (Directed Graph Shader Language) para criar um sombreador de cor simples. Esse sombreador define a cor final em um valor de cor RGB constante.

 Este documento demonstra essas atividades:

- Remover nós de um grafo

- Adicionar nós a um grafo

- Configurar propriedades de nó

- Conectar nós

## <a name="creating-a-flat-color-shader"></a>Criar um sombreador de cor simples
 Você pode implementar um sombreador de cor simples gravando o valor de cor de uma constante de cor RGB na cor de saída final.

 Antes de começar, verifique se a janela **Propriedades** e a **Caixa de Ferramentas** estão sendo exibidas.

#### <a name="to-create-a-flat-color-shader"></a>Para criar um sombreador de cor simples

1. Crie um sombreador DGSL com o qual trabalhar. Para obter informações sobre como adicionar um sombreador DGSL ao seu projeto, consulte a seção de Introdução em [Designer de Sombreador](../designers/shader-designer.md).

2. Exclua o nó **Ponto de Cor**. Use a ferramenta **Selecionar** para selecionar o nó **Ponto de Cor** e, em seguida, na barra de menus, escolha **Editar** e **Excluir**.

3. Adicione um nó **Constante de Cor** ao grafo. Na **Caixa de Ferramentas**, em **Constantes**, selecione **Constante de Cor** e mova para a superfície de design.

4. Especifique um valor de cor para o nó **Constante de Cor**. Use a ferramenta **Selecionar** para selecionar o nó **Constante de Cor** e, em seguida, na janela **Propriedades**, na propriedade **Saída**, especifique um valor de cor. Para laranja, especifique um valor de (1,0, 0,5, 0,2, 1,0).

5. Conecte a constante de cor à cor final. Para criar as conexões, mova o terminal **RGB** do nó **Constante de Cor** para o terminal **RGB** do nó **Cor Final** e, em seguida, mova o terminal **Alfa** do nó **Constante de Cor** para o terminal **Alfa** do nó **Cor Final**. Essas conexões definem a cor final para a constante de cor definida na etapa anterior.

   A ilustração a seguir mostra o grafo de sombreador concluído e uma visualização do sombreador aplicado a um cubo.

> [!NOTE]
> Na ilustração foi especificada uma cor laranja para demonstrar melhor o efeito do sombreador.

 ![Grafo de sombreador e seu resultado em um modelo de 3&#45;D](../designers/media/digit-flat-color-effect.png "Efeito de cor de dígito simples")

 Determinadas formas podem fornecer melhores visualizações para alguns sombreadores. Para obter mais informações sobre como Visualizar sombreadores no designer do sombreador, consulte [Designer de sombreador](../designers/shader-designer.md).

## <a name="see-also"></a>Consulte Também
 [Como: aplicar um sombreador a um modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [como exportar um](../designers/how-to-export-a-shader.md) [sombreador](../designers/shader-designer.md) de sombreador designer [nós designer de sombreador](../designers/shader-designer-nodes.md)
