---
title: Criando um modelo de conectividade de dados corporativos | Microsoft Docs
description: Crie um modelo de BDC (conectividade de dados corporativos) ou personalize um modelo de BDC existente usando o Visual Studio. Cada projeto do SharePoint pode conter apenas um modelo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8232847ce336ca559134aa1211a70057a1306faa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949253"
---
# <a name="create-a-business-data-connectivity-model"></a>Criar um modelo de conectividade de dados corporativos
  Você pode criar um modelo de BDC (conectividade de dados corporativos) ou personalizar um modelo de BDC existente usando o Visual Studio. Cada projeto do SharePoint pode conter apenas um modelo. Para obter mais informações, consulte [integrar dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Criar um novo modelo
 Para criar um novo modelo, crie um projeto de **modelo de conectividade de dados corporativos** ou adicione um item de **modelo de conectividade de dados corporativos** a um **projeto do SharePoint vazio**.

> [!NOTE]
> Você deve ter [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] o instalado no seu computador.

 O Visual Studio adiciona uma pasta ao projeto. Essa pasta tem o nome que você especifica para o item de **modelo de conectividade de dados corporativos** na caixa de diálogo **Adicionar novo item** . Se você criar um novo projeto de **modelo de conectividade de dados corporativos** , o Visual Studio nomeia a pasta **BdcModel1**.

 O Visual Studio adiciona os seguintes arquivos à nova pasta:

|Arquivo|Descrição|
|----------|-----------------|
|Arquivo de definição de modelo|Contém XML que define as entidades, os métodos, os objetos do sistema de linha de negócios (LOB) e outros metadados que descrevem o modelo.<br /><br /> Modifique os metadados nesse arquivo usando o BDC designer, o **BDC Explorer**, a janela **detalhes do método BDC** e a janela **Propriedades** .|
|Arquivo de código do serviço de entidade|Contém métodos que recuperam, atualizam e excluem instâncias da entidade padrão.|

 Para definir as propriedades de uma entidade, edite o arquivo de código de entidade. Para obter mais informações, consulte [como: adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Para recuperar, atualizar e excluir instâncias de uma entidade, adicione o código ao arquivo de código do serviço de entidade. Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).

 Quando você compila o projeto, o Visual Studio cria um assembly. Certifique-se de não adicionar outros itens ao projeto que adicionam código ao assembly do projeto (por exemplo: um item de **fluxo de trabalho Sequencial** ou um item de **Web Part** ). O código para esse item não será executado quando você implantar a solução porque o pacote de solução não copia o assembly para o cache de assembly global.  O pacote de solução implanta o assembly no banco de dados BDC somente no SharePoint.

> [!NOTE]
> O Visual Studio copia o assembly para ambos os locais no computador local quando você depura o projeto.

## <a name="add-an-existing-model"></a>Adicionar um modelo existente
 Você pode importar um modelo que foi criado usando outras ferramentas, como o SharePoint Designer. Você pode optar por importar um modelo existente para seu projeto nas seguintes situações:

- Para personalizar um modelo que já está implantado em um farm de servidores do SharePoint.

- Para empacotar e implantar um modelo existente em vários farms de servidores do SharePoint.

  Em ambos os casos, os sistemas LOB definidos no modelo importado não são afetados e continuarão funcionando conforme o esperado. Para adicionar um modelo existente a um projeto do SharePoint, use a caixa de diálogo **Adicionar item existente** do Visual Studio. Para obter mais informações, consulte [como: adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Você pode adicionar um sistema LOB do tipo .NET Framework assembly ao modelo importado selecionando uma opção em **Add .NET assembly LobSystem**. Isso permite que você escreva código personalizado e use um designer para definir os metadados para o modelo importado.

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Como: criar um modelo de BDC](../sharepoint/how-to-create-a-bdc-model.md)|Mostra como criar um novo modelo BDC.|
|[Como: adicionar um arquivo de modelo BDC existente a um projeto do SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Mostra como importar um modelo existente para um projeto do SharePoint.|
|[Como: usar um arquivo de recurso para especificar nomes, propriedades e permissões localizadas](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Descreve como fornecer cadeias de caracteres que são mescladas com metadados de modelo quando o modelo é consumido por uma Web Part ou página da Web.|
|[Como: incluir um assembly personalizado em um recurso do BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Mostra como incluir um assembly personalizado no recurso.|
