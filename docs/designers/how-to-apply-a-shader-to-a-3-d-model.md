---
title: Como aplicar um sombreador a um modelo 3D
description: Saiba como usar o editor de modelo para aplicar um sombreador de idioma direcionado ao sombreador de grafo a um modelo 3D para dar a ele uma aparência interessante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdaf4b86bfc773df678c03875a9ec260cd72084f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917086"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Como aplicar um sombreador a um modelo 3D

Este artigo demonstra como usar o Editor de Modelos para aplicar um sombreador DGSL (Directed Graph Shader Language) a um modelo 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Aplicar um sombreador a um modelo 3D

Você pode aplicar um efeito de sombreador a um modelo 3D para dar a ele uma aparência interessante.

Antes de começar, verifique se a janela **Propriedades** está sendo exibida.

1. Comece com uma cena 3D que contém um ou mais modelos. Se você não tiver uma cena 3D adequada, crie uma conforme descrito em [como: criar um modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md). Você também precisa ter um sombreador DGSL que possa ser aplicado ao modelo. Se você não tiver um sombreador adequado, crie um conforme a descrição em [Como criar um sombreador de cor básico](../designers/how-to-create-a-basic-color-shader.md) e salve-o em um arquivo antes de continuar.

2. No modo **Selecionar**, selecione o modelo ao qual deseja aplicar o sombreador e, na janela **Propriedades**, na propriedade **Nome do Arquivo** do grupo de propriedades **Efeito**, especifique o sombreador DGSL que deseja aplicar ao modelo.

Este é um modelo ao qual o efeito de cor básico foi aplicado:

![Cena 3&#45;D que mostra o efeito de cor básico](../designers/media/digit-3d-model-effect.png)

Depois de aplicar um sombreador a um modelo, você pode abri-lo no Designer de Sombreador selecionando o modelo e, em seguida, na janela **Propriedades**, na propriedade **(Avançado)** do grupo de propriedades **Efeito**, escolha o botão de reticências (**...**).

## <a name="see-also"></a>Consulte também

- [Como criar um modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md)
- [Como criar um sombreador de cor básico](../designers/how-to-create-a-basic-color-shader.md)
- [Editor de modelos](../designers/model-editor.md)
- [Designer de sombreador](../designers/shader-designer.md)
