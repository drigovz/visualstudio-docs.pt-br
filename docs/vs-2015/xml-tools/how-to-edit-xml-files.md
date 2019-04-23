---
title: 'Como: Editar arquivos XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92f233a036c3c0b40cbd53a298154919861b58b8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663655"
---
# <a name="how-to-edit-xml-files"></a>Como: Editar arquivos XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor XML é o novo editor para arquivos XML. Ele pode ser usado em um arquivo XML independente, ou em um arquivo associado a um projeto o Visual Studio. O Editor de XML está associado às seguintes extensões de arquivo: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings. O Editor de XML também está associado a qualquer outro tipo de arquivo que não tenha nenhum editor específico registrado e que contenha o conteúdo XML ou DTD.  
  
> [!NOTE]
>  Os documentos XHTML são tratados pelo Editor de HTML.  
  
### <a name="to-edit-an-xml-file"></a>Para editar um arquivo XML  
  
1.  Clique duas vezes no arquivo que você deseja editar.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Para adicionar um novo arquivo XML a um projeto  
  
1.  Dos **Project** menu, selecione **Adicionar Novo Item**.  
  
2.  Selecione **arquivo XML** da **modelos** painel.  
  
3.  Insira o nome do arquivo a **nome** campo e pressione **Add**.  
  
     O arquivo XML é adicionado ao projeto e aberto no Editor de XML. O arquivo contém a declaração XML padrão, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Para adicionar um arquivo XML existente a um projeto  
  
1.  Dos **Project** menu, selecione **Add Existing Item**.  
  
     O **Add Existing Item** caixa de diálogo é exibida.  
  
2.  Selecione um arquivo XML e pressione **adicionar**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Para criar um novo arquivo XML ou XSLT  
  
1.  Dos **arquivo** menu, selecione **New**.  
  
     O **novo arquivo** caixa de diálogo é exibida.  
  
2.  Selecione **arquivo XML** para criar um novo arquivo XML; ou, selecione **arquivo XSLT** para criar uma nova folha de estilos XSLT.  
  
3.  Clique em **Abrir**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Para criar um projeto para arquivos XML  
  
1.  Dos **arquivo** menu, selecione **New**e, em seguida, selecione **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione o idioma de código de sua escolha, selecione **projeto vazio**e clique em **Okey**.  
  
3.  Adicionar arquivos XML ao projeto.  
  
     O Editor de XML localiza os esquemas que você adiciona a esse projeto e os usa para validação e IntelliSense em qualquer XML, esquema ou arquivos XSLT que você editar quando o projeto for aberto.  
  
## <a name="see-also"></a>Consulte também  
 [Editor de XML](../xml-tools/xml-editor.md)   
 [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Como: criar um esquema XML de um documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
