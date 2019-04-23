---
title: 'Como: Definir uma instância de método | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 318744ec1a1a9214ce0385fc56fb1c0cf340339b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068490"
---
# <a name="how-to-define-a-method-instance"></a>Como: Definir uma instância de método
  Você deve definir pelo menos uma instância de método para cada método em seu modelo.

 Adicionar uma instância de método usando o **detalhes do método BDC** janela. Quando você adiciona a instância de método, o Visual Studio adiciona um `<MethodInstance>` elemento ao XML do arquivo de modelo em seu projeto. Para obter mais informações sobre os atributos de uma `<MethodInstance>` elemento, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

### <a name="to-define-a-method-instance"></a>Para definir uma instância de método

1. No **detalhes do método BDC** , expanda o nó de um método e, em seguida, expanda o **instâncias** nó.

2. No **adicionar uma instância de método** , escolha **criar instância de localizador**.

     Uma nova instância de método aparece sob o **instâncias** nó.

3. Na barra de menus, escolha **modo de exibição** > **janela propriedades**.

4. No **propriedades** janela, defina as propriedades da instância do método. Para obter mais informações sobre cada propriedade, consulte [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

## <a name="see-also"></a>Consulte também
- [Visão geral de ferramentas de design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Como: Adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Como: Adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Como: Definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)
