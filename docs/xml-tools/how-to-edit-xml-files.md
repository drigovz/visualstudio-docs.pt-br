---
title: 'Como: Editar arquivos XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25eebad9efc70e4fda45131e232983e81961625
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415051"
---
# <a name="how-to-edit-xml-files"></a>Como: Editar arquivos XML

O editor de XML é o novo editor para arquivos XML. Ele pode ser usado em um arquivo XML independente, ou em um arquivo associado a um projeto o Visual Studio. O editor de XML está associado com as seguintes extensões de arquivo: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *XSLT*, e *vssettings*. O editor XML também está associado a qualquer outro tipo de arquivo que não tenha nenhum editor específico registrado e que contém o conteúdo XML ou DTD.

> [!NOTE]
> Os documentos XHTML são tratados pelo Editor de HTML.

Para editar um arquivo XML, duas vezes no arquivo que você deseja editar.

## <a name="add-a-new-xml-file-to-a-project"></a>Adicionar um novo arquivo XML a um projeto

1. Dos **Project** menu, selecione **Adicionar Novo Item**.

2. Selecione **arquivo XML** da **modelos** painel.

3. Insira o nome do arquivo a **nome** campo e pressione **Add**.

   O arquivo XML é adicionado ao projeto e abre no editor de XML. O arquivo contém a declaração XML padrão, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Adicionar um arquivo XML existente a um projeto

1. Dos **Project** menu, selecione **Add Existing Item**.

   O **Add Existing Item** caixa de diálogo é exibida.

2. Selecione um arquivo XML e pressione **adicionar**.

## <a name="create-a-new-xml-or-xslt-file"></a>Crie um novo arquivo XML ou XSLT

1. Dos **arquivo** menu, selecione **New**.

   O **novo arquivo** caixa de diálogo é exibida.

2. Selecione **arquivo XML** para criar um novo arquivo XML; ou, selecione **arquivo XSLT** para criar uma nova folha de estilos XSLT.

3. Clique em **Abrir**.

## <a name="create-an-empty-project-for-xml-files"></a>Criar um projeto vazio para arquivos XML

::: moniker range="vs-2017"

1. Dos **arquivo** menu, selecione **New** > **projeto**.

   A caixa de diálogo **Novo Projeto** é exibida.

2. Selecione o idioma de código de sua escolha, selecione **projeto vazio**.

3. Clique em **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dos **arquivo** menu, selecione **New** > **projeto**.

2. Insira **projeto vazio** na caixa de pesquisa de modelo, selecione o **projeto vazio (.NET Framework)** modelo e clique **próxima**.

3. Clique em **Criar**.

::: moniker-end

4. Adicionar arquivos XML ao projeto.

   O editor de XML localiza os esquemas que você adicionar a este projeto e os usa para validação e IntelliSense em qualquer XML, esquema ou arquivos XSLT que você editar quando o projeto for aberto.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)
- [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md)
- [Como: Criar um esquema XML de um documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)