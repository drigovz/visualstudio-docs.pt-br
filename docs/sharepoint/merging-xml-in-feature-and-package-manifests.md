---
title: Mesclando XML em manifestos de recurso e pacote | Microsoft Docs
description: Merge designer – código XML gerado e adicionado pelo usuário em manifestos de pacote e recurso do SharePoint. Aprenda elementos de manifesto de pacote e recurso e exceções de mesclagem.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16305ed63f48d9f14e35aeb8d37e35f23f40be25
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304233"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Mesclar XML em manifestos de recurso e pacote
  Os recursos e pacotes são definidos por [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] arquivos de manifesto. Esses manifestos empacotados são uma combinação de dados gerados de designers e personalizados [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] inseridos no modelo de manifesto por usuários. No momento do empacotamento, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mescla as [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instruções personalizadas com o designer – fornecido [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para formar o arquivo de manifesto empacotado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . Elementos semelhantes, com as exceções observadas posteriormente em exceções de mesclagem, são mesclados para evitar [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] erros de validação depois que você implanta os arquivos no SharePoint e para tornar os arquivos de manifesto menores e mais eficientes.

## <a name="modify-the-manifests"></a>Modificar os manifestos
 Você não pode modificar diretamente os arquivos de manifesto empacotados até desabilitar o recurso ou os designers de pacote. No entanto, você pode adicionar manualmente [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos personalizados ao modelo de manifesto por meio do recurso e designers de pacote ou o [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor. Para obter mais informações, consulte [como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) e [como personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Processo de mesclagem de manifesto de pacote e recurso
 Ao combinar elementos personalizados juntamente com elementos fornecidos pelo designer, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o usa o processo a seguir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verifica se cada elemento tem um valor de chave exclusivo. Se um elemento não tiver um valor de chave exclusivo, ele será anexado ao arquivo de manifesto empacotado. Da mesma forma, os elementos que têm várias chaves não podem ser mesclados. Portanto, eles são anexados ao arquivo de manifesto.

 Se um elemento tem uma chave exclusiva, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o compara os valores do designer e das chaves personalizadas. Se os valores corresponderem, eles serão mesclados em um único valor. Se os valores forem diferentes, o valor da chave do designer será descartado e o valor da chave personalizada será usado. As coleções também são mescladas. Por exemplo, se o designer gerado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] e o personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] contiverem uma coleção de assemblies, o manifesto empacotado conterá apenas uma coleção de assemblies.

## <a name="merge-exceptions"></a>Mesclar exceções
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mescla a maioria dos [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementos do designer com elementos personalizados semelhantes, contanto que [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] eles tenham um único atributo de identificação exclusivo. No entanto, alguns elementos não têm o identificador exclusivo necessário para [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] mesclagem. Esses elementos são conhecidos como *exceções de mesclagem*. Nesses casos, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o não mescla os elementos personalizados [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] junto com os elementos fornecidos pelo designer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , mas, em vez disso, os anexa ao arquivo de manifesto empacotado.

 A seguir está uma lista de exceções de mesclagem para arquivos de manifesto de recurso e pacote [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

|Designer|Elemento XML|
|--------------|-----------------|
|Designer de recursos|ActivationDependency|
|Designer de recursos|Atualizaraction|
|Designer de pacotes|SafeControl|
|Designer de pacotes|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Elementos de manifesto de recurso
 A tabela a seguir é uma lista de todos os elementos de manifesto de recurso que podem ser mesclados e sua chave exclusiva que é usada para correspondência.

|Nome do elemento|Chave exclusiva|
|------------------|----------------|
|Recurso (todos os atributos)|*Nome do atributo* (cada nome de atributo do elemento Feature é uma chave exclusiva.)|
|ElementFile|Location|
|ElementManifests/ElementManifest|Location|
|Propriedades/Propriedade|Chave|
|CustomUpgradeAction|Nome|
|CustomUpgradeActionParameter|Nome|

> [!NOTE]
> Como a única maneira de modificar o elemento CustomUpgradeAction está no editor personalizado [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , o efeito de não mesclagem é baixo.

## <a name="package-manifest-elements"></a>Elementos de manifesto do pacote
 A tabela a seguir é uma lista de todos os elementos de manifesto do pacote que podem ser mesclados e sua chave exclusiva usada para correspondência.

|Nome do elemento|Chave exclusiva|
|------------------|----------------|
|Solução (todos os atributos)|*Nome do atributo* (cada nome de atributo do elemento da solução é uma chave exclusiva.)|
|ApplicationResourceFiles/ApplicationResourceFile|Location|
|Assemblies/assembly|Location|
|ClassResources/ClassResource|Location|
|DwpFiles/DwpFile|Location|
|FeatureManifests/FeatureManifest|Location|
|Recursos/recursos|Location|
|RootFiles/RootFile|Location|
|SiteDefinitionManifests/SiteDefinitionManifest|Location|
|WebTempFile|Location|
|TemplateFiles de modelo|Location|
|SolutionDependency|Solution|

## <a name="manually-add-deployed-files"></a>Adicionar manualmente arquivos implantados
 Alguns elementos de manifesto, como ApplicationResourceFile e DwpFiles, especificam um local que inclui um nome de arquivo. No entanto, a adição de uma entrada de nome de arquivo ao modelo de manifesto não adiciona o arquivo subjacente ao pacote. Você deve adicionar o arquivo ao projeto para incluí-lo no pacote e definir sua propriedade de tipo de implantação adequadamente.

## <a name="see-also"></a>Confira também
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Compilar e depurar soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
