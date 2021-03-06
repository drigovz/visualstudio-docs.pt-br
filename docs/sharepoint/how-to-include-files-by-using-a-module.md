---
title: 'Como: incluir arquivos usando um módulo | Microsoft Docs'
description: Saiba como incluir arquivos usando um módulo, que é um contêiner que permite implantar arquivos como páginas mestras ASPX, arquivos de texto ou imagens no SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e83a1474c7dfe6385c36cc13646bfe40fc897640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913624"
---
# <a name="how-to-include-files-by-using-a-module"></a>Como: incluir arquivos usando um módulo
  *Módulos* (não devem ser confundidos com [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) são contêineres que permitem implantar arquivos como páginas mestras aspx, arquivos de texto ou imagens no SharePoint.

 Você pode optar por implantar um arquivo em uma biblioteca de documentos ou como um arquivo normal (por exemplo, Default. aspx) fora de uma biblioteca de documentos. Para adicionar um arquivo a uma biblioteca de documentos, especifique `Type="GhostableInLibrary"` como um atributo no elemento **File** . Essa configuração instrui o SharePoint a criar um item de lista para ir com o arquivo quando ele é adicionado à biblioteca. Para implantar um arquivo fora de uma biblioteca de documentos, especifique `Type="Ghostable"` ou simplesmente omita o atributo de **tipo** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Adicionar um módulo a uma solução do SharePoint

#### <a name="to-add-a-module"></a>Para adicionar um módulo

1. No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , abra ou crie um projeto do SharePoint.

     Para obter mais informações, consulte [projeto do SharePoint e modelos de item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Em **Gerenciador de soluções**, escolha o nó do projeto e, na barra de menus, escolha **projeto**  >  **Adicionar novo item**.

     A caixa de diálogo **Adicionar novo item** é aberta.

3. Na lista de modelos do SharePoint, escolha o modelo de **módulo** e, em seguida, escolha o botão **Adicionar** .

     Esta etapa cria um nó no projeto chamado Module1.

4. Em Module1, exclua o arquivo *Sample.txt* .

     Sample.txt está incluído em todos os novos módulos, para fins de exemplo, e não é necessário. (Observe que a exclusão do arquivo também remove sua entrada do arquivo de *Elements.xml* do módulo.)

5. Se você quiser que os arquivos sejam implantados em uma determinada estrutura de pastas no SharePoint, crie essas pastas em Module1 no, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] escolhendo o nó Module1 e, na barra de menus, escolhendo **projeto**, **nova pasta**.

6. Escolha a pasta na qual você deseja adicionar o arquivo e, na barra de menus, escolha **projeto**, **Adicionar item existente**.

7. Escolha um ou mais arquivos que você deseja implantar no SharePoint e, em seguida, escolha o botão **Adicionar** .

     Quando você adiciona um arquivo ao projeto, uma entrada para ele é adicionada automaticamente ao arquivo de Elements.xml do módulo. Quando o projeto é implantado, os arquivos são copiados para o servidor do SharePoint, em relação ao diretório raiz do projeto, que é especificado pelo atributo **URL** do elemento **File** , como `Url="Module1/New Folder/SomeFile.doc` . Se você quiser alterar o local de implantação de um arquivo, mova-o para outra pasta em **Gerenciador de soluções** ou altere sua configuração de **URL** .

8. Para todos os arquivos que você deseja que apareçam em uma biblioteca de documentos, anexe o `Type="GhostableInLibrary"` atributo à sua entrada no *Elements.xml*. Por exemplo,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Implante o projeto.

     Os arquivos são copiados para os locais especificados no SharePoint.

## <a name="see-also"></a>Confira também
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
