---
title: 'Como: Adicionar um método Finder | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 49f494fa2c0fb35f7d2a65dc2ccb6b6d2d761cbe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428722"
---
# <a name="how-to-add-a-finder-method"></a>Como: Adicionar um método Finder
  Para habilitar o serviço de conectividade de dados comerciais (BDC) exibir uma lista de entidades em uma web part ou lista, você deve criar uma *Finder* método. Um método Finder é um método especial que retorna uma coleção de instâncias da entidade. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Para criar um método Finder

1. Sobre o **Designer de BDC**, escolha uma entidade.

    Para obter mais informações, confira [Como: Adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na barra de menus, escolha **modo de exibição** > **Other Windows** > **detalhes do método BDC**.

    O **detalhes do método BDC** janela é aberta. Para obter mais informações sobre o **detalhes do método BDC** janela, consulte [visão geral das ferramentas de design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. No **adicionar um método** , escolha **criar método de localizador**.

    Visual Studio adiciona um método, um parâmetro de retorno e um descritor de tipo.

4. Configure o descritor de tipo como um descritor de tipo de coleção de entidade. Para obter mais informações sobre como criar um descritor de tipo de coleção de entidade, consulte [como: Definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Não é necessário executar esta etapa se você tiver adicionado um método Finder específico à entidade. O Visual Studio usa o descritor de tipo definido no método localizador específico.

5. Na **Gerenciador de soluções**, abra o menu de atalho do serviço arquivo de código que foi gerado para a entidade e, em seguida, escolha **Exibir código**. Para obter mais informações sobre o arquivo de código de serviço, consulte [criar um modelo de conectividade de dados de negócios](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Adicione código ao método Finder. Esse código executa as seguintes tarefas:

   - Recupera dados de uma fonte de dados.

   - Retorna uma lista de entidades para o serviço de BDC.

     O exemplo a seguir retorna uma coleção de `Contact` entidades usando os dados do banco de dados de exemplo AdventureWorks para SQL Server.

   > [!NOTE]
   > Substitua o valor da `ServerName` campo com o nome do seu servidor.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Consulte também
- [Visão geral de ferramentas de design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Criar um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Como: Adicionar um método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Como: Adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Como: Adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Como: Adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Como: Adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Como: Definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)
