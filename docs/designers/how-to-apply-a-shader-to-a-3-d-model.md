---
title: Como aplicar um sombreador a um modelo 3D
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ae04f4cc0afb1c24f391d140081040efe9db50e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112761"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Como aplicar um sombreador a um modelo 3D

Este artigo demonstra como usar o Editor de Modelos para aplicar um sombreador DGSL (Directed Graph Shader Language) a um modelo 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Aplicar um sombreador a um modelo 3D

Você pode aplicar um efeito de sombreador a um modelo 3D para dar a ele uma aparência interessante.

Antes de começar, verifique se a janela **Propriedades** está sendo exibida.

1. Comece com uma cena 3D que contém um ou mais modelos. Se você não tiver uma cena 3D adequada, crie uma como descrita em [Como: Criar um modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md). Você também precisa ter um sombreador DGSL que possa ser aplicado ao modelo. Se você não tiver um sombreador adequado, crie um conforme a descrição em [Como criar um sombreador de cor básico](../designers/how-to-create-a-basic-color-shader.md) e salve-o em um arquivo antes de continuar.

2. No modo **Selecionar**, selecione o modelo ao qual deseja aplicar o sombreador e, na janela **Propriedades**, na propriedade **Nome do Arquivo** do grupo de propriedades **Efeito**, especifique o sombreador DGSL que deseja aplicar ao modelo.

Este é um modelo ao qual o efeito de cor básico foi aplicado:

![Cena 3&#45;D que mostra o efeito de cor básico](../designers/media/digit-3d-model-effect.png)

Depois de aplicar um sombreador a um modelo, você pode abri-lo no Designer de Sombreador selecionando o modelo e, em seguida, na janela **Propriedades**, na propriedade **(Avançado)** do grupo de propriedades **Efeito**, escolha o botão de reticências (**... **).

## <a name="see-also"></a>Confira também

- [Como criar um modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md)
- [Como criar um sombreador de cor básico](../designers/how-to-create-a-basic-color-shader.md)
- [Editor de modelos](../designers/model-editor.md)
- [Designer de sombreado](../designers/shader-designer.md)
