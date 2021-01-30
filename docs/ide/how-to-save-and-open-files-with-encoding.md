---
title: Como salvar e abrir arquivos com codificação
description: Saiba como salvar e abrir arquivos com codificação específica, assim, quando você abrir o arquivo, o Visual Studio exibirá o arquivo corretamente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 909e15a3acdc6725556c8d5121a363d1754a74be
ms.sourcegitcommit: cfeffe2364275a347db0ba2dce36d8e80001c081
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99104273"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Como salvar e abrir arquivos com codificação

Salve arquivos com uma codificação de caracteres específica para dar suporte a idiomas bidirecionais. Também é possível especificar uma codificação ao abrir um arquivo, para que o Visual Studio exiba o arquivo corretamente.

## <a name="to-save-a-file-with-encoding"></a>Para salvar um arquivo com codificação

1. No menu **Arquivo**, escolha **Salvar Arquivo Como** e clique no botão suspenso ao lado do botão **Salvar**.

     A caixa de diálogo **Opções de Salvamento Avançadas** é exibida.

2. Em **Codificação**, selecione a codificação a ser usada para o arquivo.

3. Opcionalmente, em **Terminações de linha**, selecione o formato para caracteres de final de linha.

     Essa opção é útil se você pretende trocar o arquivo com usuários de outro sistema operacional.

     Se deseja trabalhar com um arquivo que você sabe que está codificado de uma maneira específica, é possível informar ao Visual Studio para usar essa codificação ao abrir o arquivo. O método usado dependerá se o arquivo faz parte do projeto.

> [!NOTE]
> Se você quiser salvar o arquivo de projeto com codificação, a opção **salvar arquivo como** não estará habilitada até que você descarregue o projeto.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Para abrir um arquivo codificado que faz parte de um projeto

1. Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo e escolha **Abrir Com**.

2. Na caixa de diálogo **Abrir Com**, escolha o editor com o qual o arquivo será aberto.

     Muitos editores do Visual Studio, como o editor de formulários, detectarão a codificação automaticamente e abrirão o arquivo de forma adequada. Se você escolher um editor que permite escolher uma codificação, a caixa de diálogo **Codificação** será exibida.

3. Na caixa de diálogo **Codificação**, selecione a codificação que o editor deverá usar.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Para abrir um arquivo codificado que não faz parte de um projeto

1. No menu **Arquivo**, aponte para **Abrir**, escolha **Arquivo** ou **Arquivo da Web** e, em seguida, selecione o arquivo a ser aberto.

2. Clique no botão suspenso ao lado do botão **Abrir** e escolha **Abrir Com**.

3. Siga as Etapas 2 e 3 do procedimento anterior.

## <a name="see-also"></a>Confira também

- [Codificação e quebras de linha](encodings-and-line-breaks.md)
- [Codificação e globalização do Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizar e localizar aplicativos](../ide/globalizing-and-localizing-applications.md)
