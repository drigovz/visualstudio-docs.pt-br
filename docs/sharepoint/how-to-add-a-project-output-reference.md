---
title: 'Como: Adicione uma referência de saída do projeto | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7a26f6b2abdf0e24d4179986acc56335fb36d002
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868778"
---
# <a name="how-to-add-a-project-output-reference"></a>Como: Adicione uma referência de saída do projeto
  Para implantar assemblies de projeto não seja do SharePoint (ou arquivos. xap em projetos do Silverlight) para o SharePoint, adicioná-los como uma referência de saída do projeto.  
  
 Esse processo cria uma dependência de build de solução entre os dois projetos. Projetos associados com referências de saída do projeto são compilados antes que o projeto do SharePoint é criado e implantado.  
  
### <a name="to-add-a-project-output-reference"></a>Para adicionar uma referência de saída do projeto
  
1.  Carregar uma solução que contenha pelo menos um projeto do SharePoint e um projeto do SharePoint.  
  
2.  Na **Gerenciador de soluções**, escolha um item no nó do projeto do SharePoint.  
  
3.  No **propriedades** janela, escolha o **Project Output References** propriedade e, em seguida, escolha as reticências (![elipse do Designer de dispositivo móvel do ASP.NET](../sharepoint/media/mwellipsis.gif "ASP. Elipse de Designer de dispositivo móvel NET")) botão ao lado dele.  
  
4.  No **Project Output References** diálogo caixa, escolha o **Add** botão.  
  
5.  No painel Propriedades, escolha a seta ao lado de **tipo de implantação** propriedade e, em seguida, escolha um valor apropriado para o item não seja do SharePoint que você está fazendo referência, como **ElementFile**.  
  
6.  Escolha a seta ao lado **nome do projeto**, escolha o nome do item de projeto não seja do SharePoint e, em seguida, escolha o **Okey** botão.  
  
## <a name="see-also"></a>Consulte também
 [Fornecer informações de empacotamento e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Como: Marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
