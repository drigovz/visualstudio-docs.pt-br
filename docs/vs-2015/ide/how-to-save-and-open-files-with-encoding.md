---
title: Como salvar e abrir arquivos com codificação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9285a72137e4c2f3bdf54ef9f6535dedaa2cd5f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670772"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Como salvar e abrir arquivos com codificação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível salvar arquivos com uma codificação de caracteres específica para dar suporte a idiomas bidirecionais. Também é possível especificar uma codificação ao abrir um arquivo, para que o Visual Studio exiba o arquivo corretamente.

### <a name="to-save-a-file-with-encoding"></a>Para salvar um arquivo com codificação

1. No menu **Arquivo**, escolha **Salvar Arquivo Como** e clique no botão suspenso ao lado do botão **Salvar**.

     A caixa de diálogo **Opções de Salvamento Avançadas** é exibida.

2. Em **Codificação**, selecione a codificação a ser usada para o arquivo.

3. Opcionalmente, em **Terminações de linha**, selecione o formato para caracteres de final de linha.

     Essa opção é útil se você pretende trocar o arquivo com usuários de outro sistema operacional.

     Se deseja trabalhar com um arquivo que você sabe que está codificado de uma maneira específica, é possível informar ao Visual Studio para usar essa codificação ao abrir o arquivo. O método usado dependerá se o arquivo faz parte do projeto.

### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Para abrir um arquivo codificado que faz parte de um projeto

1. Em **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo e escolha **Abrir Com**.

2. Na caixa de diálogo **Abrir Com**, escolha o editor com o qual o arquivo será aberto.

     Muitos editores do Visual Studio, como o editor de formulários, detectarão a codificação automaticamente e abrirão o arquivo de forma adequada. Se você escolher um editor que permite escolher uma codificação, a caixa de diálogo **Codificação** será exibida.

3. Na caixa de diálogo **Codificação**, selecione a codificação que o editor deverá usar.

### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Para abrir um arquivo codificado que não faz parte de um projeto

1. No menu **Arquivo**, aponte para **Abrir**, escolha **Arquivo** ou **Arquivo da Web** e, em seguida, selecione o arquivo a ser aberto.

2. Clique no botão suspenso ao lado do botão **Abrir** e escolha **Abrir Com**.

3. Siga as Etapas 2 e 3 do procedimento anterior.

## <a name="see-also"></a>Consulte também
 [Codificação e Windows Forms](https://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9) [globalização e localização de aplicativos](../ide/globalizing-and-localizing-applications.md)
