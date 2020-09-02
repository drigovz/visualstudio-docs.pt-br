---
title: 'Como: editar arquivos XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670877"
---
# <a name="how-to-edit-xml-files"></a>Como editar arquivos XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor XML é o novo editor para arquivos XML. Ele pode ser usado em um arquivo XML independente, ou em um arquivo associado a um projeto o Visual Studio. O Editor de XML está associado às seguintes extensões de arquivo: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings. O Editor de XML também está associado a qualquer outro tipo de arquivo que não tenha nenhum editor específico registrado e que contenha o conteúdo XML ou DTD.

> [!NOTE]
> Os documentos XHTML são tratados pelo Editor de HTML.

### <a name="to-edit-an-xml-file"></a>Para editar um arquivo XML

1. Clique duas vezes no arquivo que você deseja editar.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Para adicionar um novo arquivo XML a um projeto

1. No menu **projeto** , selecione **Adicionar novo item**.

2. Selecione **arquivo XML** no painel **modelos** .

3. Insira o nome do arquivo no campo **nome** e pressione **Adicionar**.

     O arquivo XML é adicionado ao projeto e aberto no Editor de XML. O arquivo contém a declaração XML padrão, `<?xml version="1.0" encoding="utf-8" ?>`.

### <a name="to-add-an-existing-xml-file-to-a-project"></a>Para adicionar um arquivo XML existente a um projeto

1. No menu **Projeto**, selecione **Adicionar Item Existente**.

     A caixa de diálogo **Adicionar item existente** é exibida.

2. Selecione um arquivo XML e pressione **Adicionar**.

### <a name="to-create-a-new-xml-or-xslt-file"></a>Para criar um novo arquivo XML ou XSLT

1. No menu **arquivo** , selecione **novo**.

     A caixa de diálogo **Novo Arquivo** será exibida.

2. Selecione o **arquivo XML** para criar um novo arquivo XML; ou então, selecione **arquivo XSLT** para criar uma nova folha de estilo XSLT.

3. Clique em **Abrir**.

### <a name="to-create-a-project-for-xml-files"></a>Para criar um projeto para arquivos XML

1. No menu **Arquivo**, selecione **Novo** e em seguida **Projeto**.

     A caixa de diálogo **Novo Projeto** aparecerá.

2. Selecione o idioma de código de sua escolha, selecione **projeto vazio**e clique em **OK**.

3. Adicionar arquivos XML ao projeto.

     O Editor de XML localiza os esquemas que você adiciona a esse projeto e os usa para validação e IntelliSense em qualquer XML, esquema ou arquivos XSLT que você editar quando o projeto for aberto.

## <a name="see-also"></a>Consulte Também
 [XML Editor](../xml-tools/xml-editor.md) [Propriedades de documento XML do editor XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md) [como criar um esquema XML a partir de um documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
