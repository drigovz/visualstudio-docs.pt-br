---
title: Criando uma extensão com um modelo de item do editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838726"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Criando uma extensão com um modelo de item do editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar modelos de item que estão incluídos no SDK do Visual Studio para criar extensões básicas do editor que adicionam classificadores, adornos e margens ao editor. Os modelos de item do editor estão disponíveis para projetos VSIX do Visual C# ou Visual Basic.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Criando uma extensão de classificador  
 O modelo de item classificador de editor cria um classificador de editor que colore o texto apropriado (nesse caso, tudo) em qualquer arquivo de texto.  
  
1. Na caixa de diálogo **novo projeto** , expanda **Visual C#** ou **Visual Basic** e clique em **extensibilidade**. No painel **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `TestClassifier`. Clique em **OK**.  
  
2. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Vá para o nó **extensibilidade** do Visual C# e selecione **classificador de editor**. Deixe o nome de arquivo padrão (EditorClassifier1.cs).  
  
3. Há três arquivos de código, da seguinte maneira:  
  
    - EditorClassifier1.cs contém a `EditorClassifier1` classe.  
  
    - EditorClassifier1ClassificationDefinition.cs contém a `OEditorClassifier1ClassificationDefinition` classe.  
  
    - EditorClassifier1Format.cs contém a `EditorClassifier1Format`  classe.  
  
    - EditorClassifier1Provider.cs contém a `EditorClassifier1Provider` classe.  
  
4. Compile o projeto e comece a depuração. A instância experimental do Visual Studio é exibida.  
  
     Se você abrir um arquivo de texto, todo o texto será sublinhado em relação a um plano de fundo violeta.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Criando uma extensão Adornment relativa a texto  
 O modelo de texto Adornment do editor cria um Adornment relativo a texto que decora todas as instâncias do caractere de texto ' a ' usando uma caixa que tem um contorno vermelho e um plano de fundo azul. Ele é relativo a texto porque a caixa sempre sobrepõe os caracteres ' a ', mesmo quando eles são movidos ou reformatados.  
  
1. Na caixa de diálogo **novo projeto** , expanda **Visual C#** ou **Visual Basic** e clique em **extensibilidade**. No painel **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `TestAdornment`. Clique em **OK**.  
  
2. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Vá para o nó **extensibilidade** do Visual C# e selecione **texto do editor Adornment**. Deixe o nome de arquivo padrão (TextAdornment1.cs/vb).  
  
3. Há dois arquivos de código, da seguinte maneira:  
  
    - TextAdornment1.cs contém a `TextAdornment1` classe.  
  
    - extAdornment1TextViewCreationListener.cs contém a `TextAdornment1TextViewCreationListener` classe.  
  
4. Compile o projeto e comece a depuração. A instância experimental é exibida. Se você abrir um arquivo de texto, todos os caracteres ' a ' no texto serão contornados em vermelho em relação a um plano de fundo azul.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Criando uma extensão Adornment relativa ao visor  
 O modelo visor Adornment do editor cria um Adornment relativo ao visor que adiciona uma caixa violeta que tem um contorno vermelho no canto superior direito do visor.  
  
> [!NOTE]
> O *visor* é a área da exibição de texto exibida no momento.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para criar uma extensão Adornment do visor usando o modelo Adornment do visor do editor  
  
1. Na caixa de diálogo **novo projeto** , expanda **Visual C#** ou **Visual Basic** e clique em **extensibilidade**. No painel **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `ViewportAdornment`. Clique em **OK**.  
  
2. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Vá para o nó **extensibilidade** do Visual C# e selecione **Editor visor Adornment**. Deixe o nome de arquivo padrão (ViewportAdornment1.cs/vb).  
  
3. Há dois arquivos de código, da seguinte maneira:  
  
    - ViewportAdornment1.cs contém a `ViewportAdornment1` classe.  
  
    - ViewportAdornment1TextViewCreationListener.cs contém a `ViewportAdornment1TextViewCreationListener` classe  
  
4. Compile o projeto e comece a depuração. A instância experimental é exibida. Se você criar um novo arquivo de texto, uma caixa violeta que tem um contorno vermelho será exibida no canto superior direito do visor.  
  
## <a name="creating-a-margin-extension"></a>Criando uma extensão de margem  
 O modelo de margem do editor cria uma margem verde que aparece junto com as palavras "Olá, mundo!" abaixo da barra de rolagem horizontal.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para criar uma extensão de margem usando o modelo de margem do editor  
  
1. Na caixa de diálogo **novo projeto** , expanda **Visual C#** ou **Visual Basic** e clique em **extensibilidade**. No painel **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `MarginExtension`. Clique em **OK**.  
  
2. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Vá para o nó **extensibilidade** do Visual C# e selecione **Editor visor Adornment**. Deixe o nome de arquivo padrão (EditorMargin1.cs/vb).  
  
3. Há dois arquivos de código, da seguinte maneira:  
  
    - EditorMargin1.cs contém a `EditorMargin1` classe.  
  
    - EditorMargin1Factory.cs contém a `EditorMargin1Factory` classe.  
  
4. Compile este projeto e inicie a depuração. A instância experimental é exibida. Se você abrir um arquivo de texto, uma margem verde com as palavras "Olá EditorMargin1" será exibida abaixo da barra de rolagem horizontal.  
  
## <a name="see-also"></a>Consulte Também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)
