---
title: Vincular um caso de uso a documentos e diagramas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657649"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Vincular um caso de uso a documentos e diagramas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode vincular um caso de uso em um diagrama de caso de uso a outro diagrama ou documento. Por exemplo, você pode vincular o caso de uso aos diagramas e documentos a seguir:

- Um diagrama de sequência que mostra como as metas do caso de uso são realizadas por interações entre usuários e o sistema ou seus principais componentes.

- Um diagrama de atividade que mostra as ações detalhadas dos usuários e do sistema ou de seus principais componentes à medida que executam o caso de uso.

- Uma página ou um parágrafo do OneNote que descreve o caso de uso em detalhes.

- Um documento do Word ou uma apresentação do PowerPoint que descreve o caso de uso em detalhes. Você pode manter esses documentos na solução ou em um local acessível à sua equipe, como um site do SharePoint.

  Para vincular um caso de uso a um documento, você cria um artefato no diagrama de caso de uso e conecta o caso de uso ao artefato. Nas propriedades do artefato, você define o caminho do arquivo do outro diagrama ou documento. Quando você clica duas vezes no artefato, o outro diagrama ou documento é aberto.

  Você pode conectar o máximo de artefatos a cada caso de uso como desejar. Você também pode vincular artefatos a outros tipos de elemento em um diagrama de caso de uso.

### <a name="to-open-a-document-associated-with-an-artifact"></a>Para abrir um documento associado a um artefato

- No diagrama de caso de uso, clique duas vezes na forma de artefato.

     O documento associado é aberto.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Para vincular um caso de uso a um diagrama ou arquivo na mesma solução

1. Desenhe um diagrama, como um diagrama de sequência ou um diagrama de atividade, para ilustrar um cenário do caso de uso.

2. Volte para o diagrama de caso de uso.

3. Arraste o diagrama ou o arquivo de Gerenciador de Soluções para uma parte em branco do diagrama de caso de uso.

4. Conecte-se do artefato ao caso de uso usando uma **dependência**.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Para vincular a um arquivo de solução, como um documento do Word ou apresentação do PowerPoint

1. Adicione o documento à solução.

    1. Mova o documento do Word para a mesma pasta do Windows que a solução.

    2. Em Gerenciador de Soluções, clique com o botão direito do mouse na solução, aponte para **Adicionar**e clique em **Item existente**.

    3. Navegue até o documento do Word e clique em **Adicionar**.

         O documento do Word aparece em uma pasta de solução no Gerenciador de Soluções.

2. Arraste o documento do Word de Gerenciador de Soluções para uma parte em branco do diagrama de caso de uso.

     Um novo artefato é exibido.

3. Conecte-se do artefato ao caso de uso usando uma **dependência**.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Para vincular a um documento compartilhado, elemento do OneNote ou página da Web

1. Obtenha a URL do elemento compartilhado. Isso pode ser, por exemplo, um caminho de arquivo de rede que começa com ' \\ \\ ', uma página da Web ou uma URL do SharePoint começando em ' http://' ou um link para uma seção, página ou parágrafo do OneNote que comece ' OneNote: '.

2. Na caixa de ferramentas, clique em **artefato** e, em seguida, clique no diagrama de caso de uso.

3. Com o novo artefato selecionado, digite ou cole a URL na propriedade **Hyperlink** .

    > [!NOTE]
    > Se você quiser fornecer um caminho de arquivo, é melhor escolher um arquivo em um espaço de trabalho comum (começando com ' \\ \\ ') ou um arquivo em sua solução do Visual Studio. Isso garante que o caminho do arquivo permanecerá válido no computador de outro membro da equipe, ou se a solução for movida. Para adicionar um documento como um documento do Word à sua solução, clique com o botão direito do mouse na solução em Gerenciador de Soluções, aponte para **Adicionar** e clique em **Item existente**.

## <a name="see-also"></a>Consulte Também
 [Diagramas de caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md) [editar modelos UML e diagramas](../modeling/edit-uml-models-and-diagrams.md) [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md)
