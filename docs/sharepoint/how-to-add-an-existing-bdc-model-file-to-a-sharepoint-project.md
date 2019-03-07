---
title: 'Como: Adicionar um arquivo de modelo BDC existente a um projeto do SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c10dcf48e5c047778b86c524b35b4e1d5d8cc8a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614617"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Como: Adicionar um arquivo de modelo BDC existente a um projeto do SharePoint
  Você pode personalizar, empacotar e reimplantar um modelo de conectividade de dados comerciais (BDC) usando o Visual Studio para adicionar o arquivo de modelo (*BDCM*) para qualquer projeto de farm do SharePoint. Para obter mais informações, consulte [criar um modelo de conectividade de dados de negócios](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Para adicionar um arquivo de modelo BDC a um projeto do SharePoint

1. Na **Gerenciador de soluções**, escolha a pasta para um projeto do SharePoint.

2. Na barra de menus, escolha **Project** > **Add Existing Item**.

3. No **Adicionar Item existente** caixa de diálogo, navegue até o local do arquivo de definição de modelo que você deseja adicionar ao seu projeto, escolha o arquivo e, em seguida, escolha o **Add** botão.

    Se o modelo não define uma *sistema de linha de negócios (LOB) do tipo de assembly do .NET*, o **LobSystem de assembly .NET adicionar** caixa de diálogo é aberta.

4. Se a caixa de diálogo for exibida, execute uma das seguintes etapas:

   - Se você quiser escrever código personalizado e usar um designer para definir os metadados para o modelo importado, escolha o **Yes** botão, nomeie o sistema e, em seguida, escolha o **Okey** botão.

   - Caso contrário, escolha o **nenhuma** botão e, em seguida, escolha o **Okey** botão.

     O **modelo de conectividade de dados corporativos** item é adicionado ao projeto.

## <a name="see-also"></a>Consulte também
- [Criar um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Como: Criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Como: Use um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Como: Incluir um assembly personalizado em uma recurso BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
