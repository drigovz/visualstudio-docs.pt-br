---
title: Usando módulos para incluir arquivos na solução | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f8f2aa6c5d86af2424a811b6167829cefdb6fb5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985302"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Usar módulos para incluir arquivos na solução
  Pode haver ocasiões em que você talvez queira implantar arquivos no servidor do SharePoint, independentemente de seu tipo de arquivo, como novas páginas mestras. Para fazer isso, você pode usar *módulos* (não deve ser confundido com [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos de código). Os módulos são contêineres de arquivos em uma solução do SharePoint. Quando a solução é implantada, os arquivos no módulo são copiados para as pastas especificadas no servidor do SharePoint.

## <a name="module-items-and-elements"></a>Elementos e itens de módulo
 Para criar um módulo, adicione-o a um projeto escolhendo-o na caixa de diálogo **Adicionar novo item** . Em seguida, modifique seu arquivo *Elements. xml* para incluir os nomes dos arquivos que você deseja implantar, onde eles estão localizados no sistema e onde eles devem ser copiados no servidor do SharePoint.

 Aqui está um exemplo do arquivo *Elements. xml* para um módulo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Os módulos recém-criados contêm os seguintes arquivos padrão:

|Nome do Arquivo|Descrição|
|---------------|-----------------|
|*Elements. xml*|O arquivo de definição do módulo.|
|*Sample. txt*|Um arquivo de espaço reservado que serve como um exemplo de um arquivo no módulo.|

 O arquivo *Elements. xml* contém os seguintes elementos:

|Nome de elementos|Descrição|
|------------------|-----------------|
|Elementos|Contém todos os elementos definidos no módulo.|
|Módulo|O elemento Module tem um único atributo, *Name*, que especifica o nome do módulo no formato `<Module Name="Module1">`.<br /><br /> Observe que, se você alterar o nome do módulo (ou sua propriedade de *nome de pasta* ), deverá atualizar manualmente o nome no elemento de módulo.<br /><br /> Se você especificar um subdiretório para os arquivos no elemento Module, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) criará automaticamente uma estrutura de diretório correspondente para eles.|
|Arquivo|O elemento file tem dois parâmetros, *Path* e *URL*.<br /><br /> -Path: o nome e o local do arquivo na solução do SharePoint. O formato é, `Path="Module1\Sample.txt"`.<br /><br /> -URL: o local onde o arquivo será implantado no servidor do SharePoint. O formato é, `Url="Module1/Sample.txt"`.<br /><br /> -Type: um atributo opcional que tem duas configurações: *GhostableInLibrary* e *Ghostable*. O formato é, `Type="GhostableInLibrary"`. Especificar *GhostableInLibrary* significa que o arquivo será adicionado a uma biblioteca de documentos no SharePoint junto com um item de lista para acompanhar o arquivo quando ele for adicionado à biblioteca. A especificação de *fantasma* faz com que o arquivo seja adicionado ao SharePoint fora da biblioteca de documentos.|

 Cada arquivo que você deseja implantar requer uma entrada de elemento de `<File>` separada em *Elements. xml*.

## <a name="see-also"></a>Consulte também
- [Como: incluir arquivos usando um módulo](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Como provisionar um arquivo](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Criando Web Parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
