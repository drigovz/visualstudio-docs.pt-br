---
title: Dados de documentos e visualização de documentos em editores personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712140"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dados de documentos e visualização de documentos em editores personalizados
Um editor personalizado consiste em duas partes: um objeto de dados de documento e um objeto de exibição de documento. Como os nomes sugerem, o objeto de dados do documento representa os dados de texto a serem exibidos. Da mesma forma, o objeto de exibição do documento (ou "exibição") representa uma ou mais janelas nas quais exibir o objeto de dados do documento.

## <a name="document-data-object"></a>Objeto de dados de documento
 Um objeto de dados de documento é uma representação de dados de texto no buffer de texto. É um objeto COM que armazena texto de documento e outras informações. O objeto de dados do documento também lida com a persistência do documento e permite várias visualizações de seus dados. Para obter mais informações, consulte

 <xref:EnvDTE80.Window2.DocumentData%2A>e [Document Windows](../extensibility/internals/document-windows.md).

 Editores e designers personalizados <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> podem optar por usar o objeto ou seu próprio buffer personalizado. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>segue o modelo de incorporação simplificada para um editor padrão, suporta várias visualizações e fornece interfaces de eventos usadas para gerenciar várias visualizações.

## <a name="document-view-object"></a>Objeto de exibição de documento
 Uma janela que exibe código e outro texto é conhecida como exibição ou exibição de documentos. Ao criar um editor, você pode escolher uma única exibição, na qual o texto é exibido em uma única janela. Ou você pode escolher uma exibição múltipla, na qual o texto é exibido em mais de uma janela. Sua escolha depende da sua aplicação. Por exemplo, se você precisar de edição lado a lado, você escolheria exibição múltipla. Cada visualização está associada a uma entrada na tabela de documentos em execução do ambiente de desenvolvimento integrado (IDE). Ver janelas pertencem a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> um projeto ou a um objeto.

 Se o seu editor suportar várias visualizações de um objeto de dados de documento, então os dados do documento e os objetos de exibição de documentos devem ser separados. Caso contrário, eles podem ser agrupados. Para obter mais informações, consulte [Suporte a várias exibições de documentos](../extensibility/supporting-multiple-document-views.md).

 O IDE notifica as visualizações sobre eventos (por exemplo, quando uma solução contendo um documento é fechada) combinando um identificador de item (ItemID) para cada entrada na tabela de documentos em execução. Para obter mais informações sobre isso, consulte [A tabela de documentos Em execução](../extensibility/internals/running-document-table.md).

 Existem duas opções para criar uma vista para um editor personalizado. Um deles é o modelo de ativação no local, onde a exibição está hospedada em uma janela usando um controle ActiveX ou um objeto de dados de documento. O segundo é o modelo de incorporação simplificada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> onde a exibição é hospedada e é implementada para lidar com comandos de janela. Para obter informações sobre o modelo de ativação no local, consulte [ativação no local](/visualstudio/misc/in-place-activation?view=vs-2015). Para obter informações sobre o modelo simplificado de incorporação, consulte [incorporação simplificada](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Confira também

- [Suporte a várias exibições de documentos](../extensibility/supporting-multiple-document-views.md)
- [Incorporação simplificada](../extensibility/simplified-embedding.md)
- [Como: Anexar visualizações aos dados do documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Gerenciamento do suporte de bloqueio de documentos](../extensibility/document-lock-holder-management.md)
- [Exibições únicas e em várias guias](../extensibility/single-and-multi-tab-views.md)
- [Salvar um documento padrão](../extensibility/internals/saving-a-standard-document.md)
- [Persistência e a tabela de documentos em execução](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Determine qual editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
