---
title: Criando uma extensão com um modelo de item do editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739509"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Crie uma extensão com um modelo de item do editor
Você pode usar modelos de itens incluídos no Visual Studio SDK para criar extensões básicas do editor que adicionam classificadores, adornos e margens ao editor. Os modelos de itens do editor estão disponíveis para projetos Visual C# ou Visual Basic VSIX.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Crie uma extensão de classificador
 O modelo de item do Editor Classifier cria um classificador de editor que colore o texto apropriado (neste caso, tudo) em qualquer arquivo de texto.

1. Na caixa de diálogo **Novo Projeto,** expanda **visual C#** ou **Visual Basic** e clique **em Extensibility**. No **painel Templates,** selecione **Projeto VSIX**. Na caixa **Nome**, digite `TestClassifier`. Clique em **OK**.

2. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Vá para o nó de **extensibilidade** Visual C# e selecione **Editor Classifier**. Deixe o nome do arquivo padrão *(EditorClassifier1.cs).*

3. Existem quatro arquivos de código, como segue:

    - *EditorClassifier1.cs* contém `EditorClassifier1` a classe.

    - *EditorClassifier1ClassificationDefinition.cs* contém `EditorClassifier1ClassificationDefinition` a classe.

    - *EditorClassifier1Format.cs* contém `EditorClassifier1Format` a classe.

    - *EditorClassifier1Provider.cs* contém `EditorClassifier1Provider` a classe.

4. Compile o projeto e comece a depuração. A instância experimental do Visual Studio aparece.

     Se você abrir um arquivo de texto, todo o texto será sublinhado em um fundo violeta.

## <a name="create-a-text-relative-adornment-extension"></a>Crie uma extensão de adorno relativo ao texto
 O modelo De adorno de texto do editor cria um adorno relativo ao texto que decora todas as instâncias do caractere de texto 'a' usando uma caixa que tem um contorno vermelho e um fundo azul. É relativo ao texto porque a caixa sempre sobrepõe os caracteres 'a', mesmo quando eles são movidos ou reformados.

1. Na caixa de diálogo **Novo Projeto,** expanda **visual C#** ou **Visual Basic** e clique **em Extensibility**. No **painel Templates,** selecione **Projeto VSIX**. Na caixa **Nome**, digite `TestAdornment`. Clique em **OK**.

2. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Vá para o nó de **extensibilidade** Visual C# e selecione **Adorno de Texto do Editor**. Deixe o nome do arquivo padrão *(TextAdornment1.cs/vb).*

3. Existem dois arquivos de código, como segue:

    - *TextAdornment1.cs* contém `TextAdornment1` a classe.

    - *TextAdornment1TextViewCreationListener.cs* contém `TextAdornment1TextViewCreationListener` a classe.

4. Compile o projeto e comece a depuração. A instância experimental aparece. Se você abrir um arquivo de texto, todos os caracteres 'a' no texto serão delineados em vermelho contra um fundo azul.

## <a name="create-a-viewport-relative-adornment-extension"></a>Criar uma extensão de adornamento relativo à viewport
 O modelo Deadornmento do Editor Viewport cria um adorno relativo à viewport que adiciona uma caixa violeta que tem um contorno vermelho no canto superior direito da porta de exibição.

> [!NOTE]
> O **viewport** é a área da exibição de texto exibida atualmente.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para criar uma extensão de adornamento de porta de exibição usando o modelo De adornamento do Editor Viewport

1. Na caixa de diálogo **Novo Projeto,** expanda **visual C#** ou **Visual Basic** e clique **em Extensibility**. No **painel Templates,** selecione **Projeto VSIX**. Na caixa **Nome**, digite `ViewportAdornment`. Clique em **OK**.

2. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Vá para o nó de **extensibilidade** Visual C# e selecione **Adorno de Porta de Visualização do Editor**. Deixe o nome do arquivo padrão *(ViewportAdornment1.cs/vb).*

3. Existem dois arquivos de código, como segue:

    - *ViewportAdornment1.cs* contém `ViewportAdornment1` a classe.

    - *ViewportAdornment1TextViewCreationListener.cs* contém `ViewportAdornment1TextViewCreationListener` a classe

4. Compile o projeto e comece a depuração. A instância experimental aparece. Se você criar um novo arquivo de texto, uma caixa violeta que tenha um contorno vermelho será exibida no canto superior direito da porta de exibição.

## <a name="create-a-margin-extension"></a>Criar uma extensão de margem
 O modelo Margem do Editor cria uma margem verde que aparece junto com as palavras **Olá mundo!* abaixo da barra de rolagem horizontal.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para criar uma extensão de margem usando o modelo Margem do Editor

1. Na caixa de diálogo **Novo Projeto,** expanda **visual C#** ou **Visual Basic** e clique **em Extensibility**. No **painel Templates,** selecione **Projeto VSIX**. Na caixa **Nome**, digite `MarginExtension`. Clique em **OK**.

2. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Vá para o nó de **extensibilidade** Visual C# e selecione **Margem do Editor**. Deixe o nome do arquivo padrão (EditorMargin1.cs/vb).

3. Existem dois arquivos de código, como segue:

    - *EditorMargin1.cs* contém `EditorMargin1` a classe.

    - *EditorMargin1Factory.cs* contém `EditorMargin1Factory` a classe.

4. Construa este projeto e comece a depurar. A instância experimental aparece. Se você abrir um arquivo de texto, uma margem verde que tenha as palavras **Hello EditorMargin1** será exibida abaixo da barra de rolagem horizontal.

## <a name="see-also"></a>Confira também
- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
