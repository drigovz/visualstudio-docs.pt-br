---
title: 'Como: Adicionar uma entidade a um modelo | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a51786cc8a448bf8b7348917df58cef43468619
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609651"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Como: Adicionar uma entidade a um modelo
  Para criar uma entidade, adicione um controle de entidade do Visual Studio **caixa de ferramentas** para o designer de conectividade de dados comerciais (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Para adicionar uma entidade no modelo

1.  Criar um projeto BDC ou abrir um projeto existente do BDC. Para obter mais informações, consulte [criar um modelo de conectividade de dados de negócios](../sharepoint/creating-a-business-data-connectivity-model.md).

2.  No **caixa de ferramentas**, da **BusinessDataCatalog** de grupo, adicione um **entidade** controle para o designer.

     A nova entidade é exibida no designer. O Visual Studio adiciona um `<Entity>` elemento ao XML do arquivo de modelo BDC em seu projeto. Para obter mais informações sobre os atributos de um elemento de entidade, consulte [entidade](http://go.microsoft.com/fwlink/?LinkId=169296).

3.  No designer, abra o menu de atalho para a entidade, escolha **Add**e, em seguida, escolha **identificador**.

     Um novo identificador aparece na entidade.

    > [!NOTE]
    >  Você pode alterar o nome da entidade e o identificador na **propriedades** janela.

4.  Defina os campos da entidade em uma classe. Você pode adicionar uma nova classe ao projeto ou usar uma classe existente criada usando outras ferramentas, como o Object Relational Designer (O/R Designer). O exemplo a seguir mostra uma classe de entidade chamada contato.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Consulte também
- [Como: Adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Como: Adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Como: Adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Como: Adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Como: Adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
