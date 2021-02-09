---
title: 'Designer de pacotes: Adicionar & remover recursos e itens para pacote'
titleSuffix: ''
description: Examine como adicionar e remover recursos e itens para um pacote do SharePoint usando o designer de pacotes no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 92503d8e29bac4f44df5376f3cecb24247b585d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923593"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Como adicionar e remover recursos e itens para um pacote usando o designer de pacotes
  Quando você cria uma solução do SharePoint, o Visual Studio adiciona os recursos padrão do SharePoint ao pacote na solução. Antes da implantação final, você pode adicionar e remover itens e recursos de projeto do SharePoint para modificar o pacote do SharePoint.

 Como alternativa, você pode usar o Gerenciador de empacotamento para adicionar e remover itens de projeto do SharePoint. Você também pode exibir e alterar a hierarquia dos itens e recursos de projeto do SharePoint que são colocados no pacote (. wsp). Para obter mais informações, consulte [como adicionar e remover recursos e itens para um pacote usando o Gerenciador de empacotamento](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Adicionar recursos a um pacote do SharePoint
 Você pode usar o designer de pacote para adicionar recursos a um pacote do SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Para adicionar recursos do SharePoint com o designer de pacotes

1. Abra o **Designer de pacotes**.

    Para obter mais informações, consulte [como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Adicione um ou mais recursos do SharePoint executando uma ou mais das seguintes etapas:

   1. Clique duas vezes em cada item nos **itens da** lista de solução que você deseja adicionar.

   2. Escolha um item que você deseja adicionar e, em seguida, escolha o botão **Adicionar** (>).

   3. Escolha o botão **Adicionar tudo** (>>) para adicionar todos os itens de uma vez.

      Por exemplo, você pode clicar duas vezes em um item nos **itens na** lista de soluções para adicioná-lo aos **itens na** lista de pacotes.

      Os itens e recursos de projeto do SharePoint aparecem nos **itens da lista pacote** .

## <a name="remove-features-from-a-sharepoint-package"></a>Remover recursos de um pacote do SharePoint
 Você pode usar o designer de pacote para remover recursos para um pacote do SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Para remover recursos do SharePoint com o designer de pacotes

1. Nos **itens na lista pacote** , escolha um item que você deseja remover e, em seguida, escolha o botão **remover** (<) ou escolha o botão **remover tudo** (<<) para remover todos os itens.

     Os itens do SharePoint aparecem nos **itens da** lista de soluções.

## <a name="see-also"></a>Confira também
- [Criar pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Como: criar um pacote](/previous-versions/ee231585(v=vs.110))