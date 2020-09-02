---
title: Visão geral das ferramentas de design de modelo do BDC | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a2531f1cc6352a03acf0b3d6af82c35e47c2743
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827945"
---
# <a name="bdc-model-design-tools-overview"></a>Visão geral das ferramentas de design de modelo do BDC
  Você pode criar um modelo de BDC (conectividade de dados corporativos) usando o designer do BDC, a janela **detalhes do método BDC** e o **Gerenciador do BDC**.

 O **BDC Explorer** permite que você procure o modelo, pesquise o modelo e defina descritores de tipo.

## <a name="bdc-designer"></a>Designer de BDC
 O BDC designer permite que você defina as entidades em seu modelo e organize visualmente suas relações umas com as outras. Use o BDC designer para realizar as seguintes tarefas:

- Adicione entidades ao modelo.

- Remova as entidades do modelo.

- Defina relações entre entidades.

  Para abrir o designer do BDC, clique duas vezes no arquivo de modelo em seu projeto ou abra o menu de atalho para o arquivo de modelo e, em seguida, escolha **abrir**. Adicione uma entidade ao modelo arrastando ou copiando uma **entidade** da **caixa de ferramentas** para o designer. Para criar uma associação entre duas entidades, escolha o controle de **Associação** na **caixa de ferramentas**, escolha a primeira entidade e, em seguida, escolha a segunda entidade.

## <a name="bdc-method-details-window"></a>Janela detalhes do método BDC
 Use a janela **detalhes do método BDC** para definir os parâmetros, as instâncias e os descritores de filtro de um método.

 Você pode gerar rapidamente os métodos Finder, Finder, Creator, Updater e excluidor na janela detalhes do **método do BDC** . Quando você gera esses métodos, o Visual Studio adiciona metadados, como parâmetros, instâncias e descritores de tipo, ao método. Você pode modificar esses metadados para atender ao seu cenário específico.

 Para abrir a janela **detalhes do método do BDC** , na barra de menus, escolha **Exibir**  >  outros detalhes do método do**Windows**  >  **BDC**.

 Para exibir os métodos na janela **detalhes do método BDC** , escolha a entidade no designer do BDC. Os métodos da entidade selecionada aparecem na janela **detalhes do método do BDC** . Se você não escolher uma entidade no designer do BDC, a janela **detalhes do método BDC** não exibirá nenhuma informação.

 Expanda ou recolha nós na janela **detalhes do método BDC** para definir parâmetros, instâncias e descritores de filtro. Use o **Gerenciador do BDC** para definir descritores de tipo.

## <a name="bdc-explorer"></a>BDC Explorer
 O **BDC Explorer** exibe os elementos que compõem o modelo. Para abrir o **BDC Explorer**, na barra de menus, escolha **Exibir**  >  **outro Windows**  >  **BDC Explorer**. Para procurar o modelo, expanda nós no **BDC Explorer**. Cada nó representa um elemento no XML do arquivo de modelo.

 À medida que você escolhe os nós no **Gerenciador do BDC**, as propriedades de cada nó que você escolhe aparecem na janela **Propriedades** . Muitas dessas propriedades correspondem aos atributos no arquivo de modelo. Você pode pesquisar o modelo usando a caixa de pesquisa na parte superior do **BDC Explorer**.

> [!NOTE]
> O **BDC Explorer** não exibe identificadores, propriedades personalizadas, cadeias de caracteres localizadas, grupos de associação, ações, descritores de filtro, listas de controle de ação e os valores de parâmetro padrão.

### <a name="define-type-descriptors"></a>Definir descritores de tipo
 Use o **Gerenciador do BDC** para definir descritores de tipo. O Gerenciador do BDC permite que você defina um descritor de tipo uma vez e, em seguida, reutilize esse descritor em outro lugar em seu modelo. Para fazer isso, copie um descritor de tipo e cole-o em qualquer outro parâmetro ou descritor de tipo.

> [!NOTE]
> As alterações em um descritor de tipo original não afetam as cópias desse descritor de tipo.

 Para obter mais informações, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Confira também
- [Como: criar um modelo de BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Como: adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Como adicionar um método localizador](../sharepoint/how-to-add-a-finder-method.md)
- [Como adicionar um método localizador específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Como: adicionar um método de criador](../sharepoint/how-to-add-a-creator-method.md)
- [Como adicionar um método excluidor](../sharepoint/how-to-add-a-deleter-method.md)
- [Como adicionar um método de atualizador](../sharepoint/how-to-add-an-updater-method.md)
- [Criar uma associação entre entidades](../sharepoint/creating-an-association-between-entities.md)
- [Walkthrough: criar uma lista externa no SharePoint usando dados corporativos](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integre dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)
