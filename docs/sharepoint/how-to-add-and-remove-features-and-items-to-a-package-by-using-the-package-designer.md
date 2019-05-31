---
title: 'Designer de pacote: Adicionar e remover funcionalidades e itens de pacote'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbd44bbf3b337815c8c72cea66dd4d56fc645ade
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401609"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Como: Adicionar e remover funcionalidades e itens de um pacote usando o Designer de pacote
  Quando você cria uma solução do SharePoint, o Visual Studio adiciona os recursos do SharePoint padrão para o pacote da solução. Antes da implantação final, você pode adicionar e remover itens de projeto do SharePoint e recursos para modificar o pacote do SharePoint.

 Como alternativa, você pode usar o Packaging Explorer para adicionar e remover itens de projeto do SharePoint. Você também pode exibir e alterar a hierarquia dos itens de projeto do SharePoint e recursos que são colocados no pacote (. wsp). Para obter mais informações, confira [Como: Adicionar e remover funcionalidades e itens de um pacote usando o Packaging Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Adicionar recursos a um pacote do SharePoint
 Você pode usar o Designer de pacote para adicionar recursos a um pacote do SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Para adicionar recursos do SharePoint com o designer de pacote

1. Abra o **Designer de pacote**.

    Para obter mais informações, confira [Como: Personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Adicione um ou mais recursos do SharePoint, executando uma ou mais das seguintes etapas:

   1. Clique duas vezes em cada item na **itens na solução** lista que você deseja adicionar.

   2. Escolha um item que você deseja adicionar e, em seguida, escolha o **adicionar** botão (>).

   3. Escolha o **Adicionar tudo** botão (>>) para adicionar todos os itens ao mesmo tempo.

      Por exemplo, você pode clicar duas vezes em um item de **itens na solução** lista para adicioná-lo para o **itens do pacote** lista.

      Os itens de projeto do SharePoint e recursos aparecem na **itens do pacote** lista.

## <a name="remove-features-from-a-sharepoint-package"></a>Remover recursos de um pacote do SharePoint
 Você pode usar o Designer de pacote para remover os recursos para um pacote do SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Para remover recursos do SharePoint com o designer de pacote

1. No **itens do pacote** , escolha um item que você deseja remover e, em seguida, escolha o **remover** (<) botão ou escolha o **remover tudo** botão (<<) para remover todos os itens.

     Os itens do SharePoint aparecem na **itens na solução** lista.

## <a name="see-also"></a>Consulte também
- [Criar pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Como: Personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Como: Criar um pacote](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
