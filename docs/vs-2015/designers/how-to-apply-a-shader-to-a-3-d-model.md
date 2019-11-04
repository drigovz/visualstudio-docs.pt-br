---
title: 'Como: Aplicar um sombreador a um modelo 3D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15d88f52b3af3a3e4502c618280107a882761259
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664611"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Como: Aplicar um sombreador a um modelo 3D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este documento demonstra como usar o Editor de Modelos para aplicar um sombreador DGSL (Directed Graph Shader Language) a um modelo 3D.

 Este documento demonstra esta atividade:

- Aplicar um sombreador a um modelo 3D

## <a name="applying-a-shader-to-a-3-d-model"></a>Aplicar um sombreador a um modelo 3D
 Você pode aplicar um efeito de sombreador a um modelo 3D para dar a ele uma aparência interessante.

 Antes de começar, verifique se a janela **Propriedades** está sendo exibida.

#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Para aplicar um sombreador a um modelo 3D

1. Comece com uma cena 3D que contém um ou mais modelos. Se você não tiver uma cena 3-D adequada, crie uma conforme descrito em [How para: Crie um ](../designers/how-to-create-a-basic-3-d-model.md) de modelo 3D básico. Você também precisa ter um sombreador DGSL que possa aplicar ao modelo. Se você não tiver um sombreador adequado, crie um conforme a descrição em [Como: Crie um sombreador de cores básico ](../designers/how-to-create-a-basic-color-shader.md) e verifique se você o salvou em um arquivo antes de continuar.

2. No modo **Selecionar**, selecione o modelo ao qual deseja aplicar o sombreador e, na janela **Propriedades**, na propriedade **Nome do Arquivo** do grupo de propriedades **Efeito**, especifique o sombreador DGSL que deseja aplicar ao modelo.

   Este é um modelo ao qual o efeito de cor básico foi aplicado:

   ![cena&#45;3 D que mostra o efeito de cor básico](../designers/media/digit-3d-model-effect.png "Dígito 3D-efeito de modelo")

   Depois de aplicar um sombreador a um modelo, você pode abri-lo no Designer de Sombreador selecionando o modelo e, em seguida, na janela **Propriedades**, na propriedade **(Avançado)** do grupo de propriedades **Efeito**, escolha o botão de reticências ( **...** ).

## <a name="see-also"></a>Consulte também
 [Como: Crie um modelo 3D básico ](../designers/how-to-create-a-basic-3-d-model.md) [How para: Criar um sombreador de cores básico ](../designers/how-to-create-a-basic-color-shader.md) [Designer de sombreador](../designers/shader-designer.md) do [Editor de modelos](../designers/model-editor.md)
