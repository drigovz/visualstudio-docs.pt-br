---
title: Criando recursos do SharePoint | Microsoft Docs
description: Crie um recurso do SharePoint para agrupar itens de projeto do SharePoint relacionados para facilitar a implantação. Adicione recursos à solução do SharePoint. Use o designer de recursos.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06a8fdef9c194e9b0f81768f93b675ade77d39ef
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850579"
---
# <a name="create-sharepoint-features"></a>Criar recursos do SharePoint
  Você pode usar um recurso do SharePoint para agrupar itens de projeto do SharePoint relacionados para facilitar a implantação. Você pode criar recursos, definir escopos e marcar outros recursos como dependências usando o designer de recursos do SharePoint. O designer também gera um manifesto, que é um arquivo XML que descreve cada recurso.

## <a name="add-features-to-the-sharepoint-solution"></a>Adicionar recursos à solução do SharePoint
 Você pode adicionar um recurso à solução do SharePoint usando Gerenciador de Soluções ou o Gerenciador de empacotamento. Você pode usar um dos métodos a seguir para adicionar um recurso.

- No **Gerenciador de soluções**, abra o menu de atalho para **recursos** e, em seguida, escolha **Adicionar recurso**.

- No **Packaging Explorer**, abra o menu de atalho para o pacote e escolha **Adicionar recurso**.

## <a name="using-the-feature-designer"></a>Usando o designer de recursos
 Uma solução do SharePoint pode conter um ou mais recursos do SharePoint, que são agrupados sob o nó de recurso no Gerenciador de Soluções. Cada recurso tem seu próprio **Designer de recursos** que você pode usar para personalizar as propriedades do recurso. Para obter mais informações, consulte [como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Para diferenciar os recursos uns dos outros, você pode configurar as propriedades do recurso, como título, descrição, versão e escopo.

### <a name="feature-designer-options"></a>Opções do designer de recursos
 Depois de criar um recurso, você pode usar o designer de recursos para personalizá-lo.

 A tabela a seguir descreve as propriedades de recurso que são exibidas no designer de recursos.

|Propriedade|Descrição|
|--------------|-----------------|
|Título|Opcional. O título padrão do recurso é definido como *SolutionName* *FeatureName*.|
|Descrição|Opcional. A descrição do recurso do SharePoint.|
|Escopo|Obrigatórios. Se um recurso for criado usando **Gerenciador de soluções**, o escopo será definido como Web por padrão.<br /><br /> -Farm: Ative um recurso para um farm de servidores inteiro.<br /><br /> -Site: Ative um recurso para todos os sites em um conjunto de sites.<br /><br /> -Web: ativar um recurso para um site específico.<br /><br /> -WebApplication: ativar um recurso para todos os sites em um aplicativo Web.|
|Itens na solução|Todos os itens do SharePoint que podem ser adicionados ao recurso.|
|Itens no recurso|Os itens de projeto do SharePoint que foram adicionados ao recurso.|

## <a name="add-and-remove-sharepoint-project-items"></a>Adicionar e remover itens de projeto do SharePoint
 Você pode selecionar quais itens de projeto do SharePoint para os quais deseja adicionar um recurso do SharePoint para implantação. Use o **Designer de recursos** para adicionar e remover itens de recursos e exibir o manifesto do recurso. Para obter mais informações, consulte [como: Adicionar e remover itens para recursos do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Adicionar dependências de recurso
 Você pode configurar o manifesto de recurso para que o servidor do SharePoint ative determinados recursos antes de o recurso ser ativado. Por exemplo, se o recurso do SharePoint depender de outros recursos de funcionalidade ou dados, o servidor do SharePoint poderá primeiro tentar ativar qualquer um dos recursos dos quais o recurso depende. Para obter mais informações, consulte [como: Adicionar e remover dependências de recursos](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Confira também
- [Como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Como: Adicionar e remover itens para recursos do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Como: Adicionar e remover dependências de recursos](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
