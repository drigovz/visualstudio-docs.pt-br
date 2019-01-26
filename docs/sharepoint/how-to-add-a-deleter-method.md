---
title: 'Como: Adicionar um método Deleter | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cad4de5ed1b31d02d9136b5ec2b46be71f54fea4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870877"
---
# <a name="how-to-add-a-deleter-method"></a>Como: Adicionar um método Deleter
  Você pode habilitar um usuário final excluir um registro de dados de uma lista externa em um site do SharePoint, adicionando um método Deleter ao modelo. Para obter mais informações, consulte [criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Para criar um método Deleter  
  
1. Sobre o **Designer de BDC**, escolha uma entidade.  
  
2. Na barra de menus, escolha **modo de exibição** > **Other Windows** > **detalhes do método BDC**.  
  
    O **detalhes do método BDC** janela é aberta. Para obter mais informações sobre essa janela, consulte [visão geral das ferramentas de design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. No **adicionar um método** , escolha **criar um método Deleter**.  
  
    Visual Studio adiciona os seguintes elementos ao modelo. Esses elementos aparecem na **detalhes do método BDC** janela.  
  
   - Um método chamado **excluir**.  
  
   - Um parâmetro de entrada para o método.  
  
   - Um descritor de tipo para o parâmetro.  
  
   - Uma instância de método para o método.  
  
     Para obter mais informações, consulte [criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. Na **Gerenciador de soluções**, abra o menu de atalho do serviço arquivo de código que foi gerado para a entidade e, em seguida, escolha **Exibir código**.  
  
    O arquivo de código do serviço de entidade é aberto no Editor de códigos. Para obter mais informações sobre o arquivo de código do serviço de entidade, consulte [criar um modelo de conectividade de dados de negócios](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Adicione código ao método de agente de exclusão para excluir um registro. O exemplo a seguir exclui um item de linha de um pedido de vendas usando o banco de dados de exemplo AdventureWorks para SQL Server.  
  
   > [!NOTE]  
   >  O método neste exemplo usa dois parâmetros de entrada.  
  
   > [!NOTE]  
   >  Substitua o valor da `ServerName` campo com o nome do seu servidor.  
  
    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>Consulte também
 [Criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Como: Adicionar um método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Como: Adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Como: Adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Como: Adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Visão geral de ferramentas de design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: Adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Como: Definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)  
