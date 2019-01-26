---
title: 'Como: Adicionar um parâmetro a um método | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d55c345d9cd0e57d7af2ed359cf4bd9a4f06cd9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868112"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Como: Adicionar um parâmetro a um método
  Use um parâmetro para passar informações para o método ou para retornar informações de um método. Todos os métodos devem ter pelo menos um parâmetro. Para obter mais informações sobre como criar um parâmetro para dar suporte o tipo de método que você deseja criar, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando você adiciona um parâmetro para um método, o Visual Studio adiciona o elemento de parâmetro para o XML do arquivo de modelo em seu projeto. Para obter mais informações sobre os atributos de um elemento de parâmetro, consulte [parâmetro](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Para adicionar um parâmetro a um método  
  
1.  Adicione um método a uma entidade.  
  
2.  Na barra de menus, escolha **modo de exibição** > **Other Windows** > **detalhes do método BDC**.  
  
     O **detalhes do método BDC** janela é aberta. Para obter mais informações, consulte [visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  No **detalhes do método BDC** , expanda o nó do método e, em seguida, expanda o **parâmetros** nó.  
  
4.  No **adicionar um parâmetro** , escolha **criar parâmetro**.  
  
     Um novo parâmetro aparece sob o **parâmetros** nó.  
  
5.  Na barra de menus, escolha **modo de exibição** > **janela propriedades**.  
  
6.  No **propriedades** janela, defina as **nome** propriedade para qualquer nome que faça sentido. Por exemplo, se o método retornará os clientes, você pode nomear o método **GetCustomers**.  
  
7.  No **detalhes do método BDC** janela, abra a lista que aparece para a direção do parâmetro e, em seguida, escolha **na**, **InOut**, **Out**, ou **retornar**.  
  
     Para obter mais informações sobre a direção de escolha para o método de tipo que você está criando, consulte [criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modificar o descritor de tipo do parâmetro. Para obter mais informações, confira [Como: Definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Consulte também
 [Visão geral de ferramentas de design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Como: Adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Como: Definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Como: Definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)   
 [Criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)  
