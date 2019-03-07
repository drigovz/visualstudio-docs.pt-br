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
ms.openlocfilehash: 569f1027163d5651d184254b4e6f57a02df2a39a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596179"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Usar módulos para incluir arquivos na solução
  Pode haver ocasiões quando você talvez queira implantar arquivos para o servidor do SharePoint, independentemente de seu tipo de arquivo, como novas páginas mestras. Para fazer isso, você pode usar *módulos* (não deve ser confundido com [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos de código). Módulos são contêineres para arquivos em uma solução do SharePoint. Quando a solução é implantada, os arquivos no módulo são copiados para as pastas especificadas no servidor do SharePoint.

## <a name="module-items-and-elements"></a>Elementos e itens de módulo
 Para criar um módulo, adicioná-lo a um projeto, escolhendo-o na **Adicionar Novo Item** caixa de diálogo. Em seguida, modifique seus *Elements. XML* arquivo para incluir os nomes dos arquivos que você deseja implantar, onde estão localizados no sistema, e onde eles devem ser copiados no servidor do SharePoint.

 Aqui está um exemplo de como o *Elements. XML* arquivo para um módulo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Recém-criado módulos contêm os seguintes arquivos padrão:

|Nome do Arquivo|Descrição|
|---------------|-----------------|
|*Elements.xml*|O arquivo de definição para o módulo.|
|*Exemplo. txt*|Um arquivo de espaço reservado que serve como um exemplo de um arquivo no módulo.|

 O *Elements. XML* arquivo contém os seguintes elementos:

|Nome de elementos|Descrição|
|------------------|-----------------|
|Elementos|Contém todos os elementos definidos no módulo.|
|Módulo|O elemento de módulo tem um único atributo, *nome*, que especifica o nome do módulo no formato `<Module Name="Module1">`.<br /><br /> Observe que, se você alterar o nome do módulo (ou seus *nome da pasta* propriedade), você deve atualizar manualmente o nome no elemento do módulo.<br /><br /> Se você especificar um subdiretório para o arquivo (s) no elemento de módulo, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) criará automaticamente uma estrutura de diretório correspondente para eles.|
|Arquivo|O elemento de arquivo tem dois parâmetros, *caminho* e *Url*.<br /><br /> -Path: O nome e o local do arquivo na solução do SharePoint. O formato é, `Path="Module1\Sample.txt"`.<br /><br /> -Url: O local onde o arquivo será implantado no servidor do SharePoint. O formato é, `Url="Module1/Sample.txt"`.<br /><br /> -Tipo: Um atributo opcional que tem duas configurações: *GhostableInLibrary* e *Ghostable*. O formato é, `Type="GhostableInLibrary"`. Especificando *GhostableInLibrary* significa que o arquivo será adicionado à biblioteca de documentos no SharePoint junto com um item de lista para acompanhar o arquivo quando ele é adicionado à biblioteca. Especificando *Ghostable* faz com que o arquivo a ser adicionado ao SharePoint fora da biblioteca de documentos.|

 Cada arquivo que você deseja implantar requer um separado `<File>` entrada de elemento no *Elements. XML*.

## <a name="see-also"></a>Consulte também
- [Como: Incluir arquivos usando um módulo](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Como: Provisionar um arquivo](http://go.microsoft.com/fwlink/?LinkID=144271)
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Criando web parts para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
