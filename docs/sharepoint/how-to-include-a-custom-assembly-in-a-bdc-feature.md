---
title: 'Como: Incluir um Assembly personalizado em uma recurso BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: efbbef540ddd7759fe0614eecccc663368bd23b8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633610"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Como: Incluir um assembly personalizado em uma recurso BDC
  Seu projeto pode fazer referência a assemblies de outros projetos na mesma solução. No entanto, você deve adicionar esses assemblies para o arquivo de recurso do projeto usando o **Assign referenciado assemblies para o LobSystems** caixa de diálogo.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Para incluir um assembly personalizado em um recurso de conectividade (BDC) de dados de negócios

1.  Na **Gerenciador de soluções**, escolha a pasta que contém o modelo BDC.

2.  Sobre o **modo de exibição** menu, clique em **janela propriedades**.

3.  No **propriedades** janela, escolha o **Assemblies** propriedade e, em seguida, no botão de reticências (![elipse do Designer de dispositivo móvel do ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET para dispositivos móveis Elipse de Designer")).

     O **Assign referenciado assemblies para o LobSystems** caixa de diálogo é exibida.

4.  No **selecione um Assembly** , escolha o assembly personalizado.

    > [!NOTE]
    >  Assemblies são exibidas somente na **Assign referenciado assemblies para o LobSystems** caixa de diálogo se você tiver adicionado uma referência ao projeto que contém o assembly. Para obter mais informações, confira [Como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5.  No **propriedades de referência** grupo, abra a lista que aparece para o **escopo do LobSystem** propriedade, escolha o sistema LOB dos métodos que usam o assembly personalizado e, em seguida, escolha o **Okey**  botão.

    > [!NOTE]
    >  Para depurar o código no assembly personalizado, você deve adicionar o assembly para o pacote de solução. Para obter mais informações, confira [Como: Adicionar e remover assemblies adicionais](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Consulte também
- [Como: Use um arquivo de recurso para especificar nomes localizados, propriedades e permissões](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Como: Adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Criar um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Como: Criar um modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Dados de negócios Integragte no SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
