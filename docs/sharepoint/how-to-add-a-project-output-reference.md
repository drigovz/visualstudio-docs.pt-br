---
title: 'Como: adicionar uma referência de saída de projeto | Microsoft Docs'
description: Aprenda a adicionar uma referência de saída de projeto para que você possa implantar assemblies de projeto não SharePoint (ou arquivos. xap em projetos do Silverlight) no SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 03980eea9d16cde2b6f079e0b33973958fed7a7f
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849864"
---
# <a name="how-to-add-a-project-output-reference"></a>Como: adicionar uma referência de saída de projeto
  Para implantar assemblies de projeto não SharePoint (ou arquivos. xap em projetos do Silverlight) no SharePoint, adicione-os como uma referência de saída de projeto.

 Esse processo cria uma dependência de compilação de solução entre os dois projetos. Os projetos associados às referências de saída do projeto são criados antes que o projeto do SharePoint seja compilado e implantado.

### <a name="to-add-a-project-output-reference"></a>Para adicionar uma referência de saída de projeto

1. Carregue uma solução que contenha pelo menos um projeto do SharePoint e um projeto que não seja do SharePoint.

2. Em **Gerenciador de soluções**, escolha um item no nó do projeto do SharePoint.

3. Na janela **Propriedades** , escolha a propriedade de **referências de saída do projeto** e, em seguida, escolha o botão de reticências (elipse do ![Designer móvel ASP.net](../sharepoint/media/mwellipsis.gif "Elipse do designer móvel ASP.NET")) ao lado dele.

4. Na caixa de diálogo **referências de saída do projeto** , escolha o botão **Adicionar** .

5. No painel Propriedades, escolha a seta ao lado da propriedade **tipo de implantação** e, em seguida, escolha um valor apropriado para o item não SharePoint que você está referenciando, como **ElementFile**.

6. Escolha a seta ao lado de **nome do projeto**, escolha o nome do item de projeto não SharePoint e, em seguida, escolha o botão **OK** .

## <a name="see-also"></a>Confira também
- [Fornecer informações de empacotamento e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Como: marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
