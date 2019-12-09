---
title: Especificando eventos de build personalizados
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fabbd4dc42ac4f66c7f53b639c6e7ed1f432878c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667122"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Especificando eventos de build personalizados no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao especificar um evento de build personalizado, é possível executar comandos automaticamente antes do início de um build ou após sua conclusão. Por exemplo, é possível executar um arquivo .bat antes do início de um build ou copiar novos arquivos para uma pasta após sua conclusão. Eventos de build serão executados somente se o build atingir com êxito esses pontos no processo de build.

 Para obter informações específicas sobre a linguagem de programação que está sendo usada, consulte os seguintes tópicos:

- Visual Basic – [Como especificar eventos de build (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- Visual C# e F # – [Como especificar eventos de build (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ – [Especificando eventos de build](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Sintaxe
 Os eventos de build seguem a mesma sintaxe dos comandos do DOS, mas é possível usar macros para criar eventos de build com mais facilidade. Para obter uma lista das macros disponíveis, consulte [Caixa de diálogo Linha de Comando do Evento de Pré-build/Evento de Pós-build](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Para obter melhores resultados, siga estas dicas de formatação:

- Adicione uma instrução `call` antes de todos os eventos de build que executam arquivos .bat.

     Exemplo: `call C:\MyFile.bat`

     Exemplo: `call C:\MyFile.bat call C:\MyFile2.bat`

- Coloque os caminhos de arquivo entre aspas.

     Exemplo (para [!INCLUDE[win8](../includes/win8-md.md)]): “%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe” – se “$(TargetPath)”

- Separe vários comandos usando quebras de linha.

- Inclua curingas, conforme necessário.

     Exemplo: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

    > [!NOTE]
    > `%I` no código acima deve ser `%%I` em scripts em lote.

## <a name="see-also"></a>Consulte também
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md) [caixa de diálogo de linha de comando do evento de eventos/pós-build de pré-compilação](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md) [passo a passo: Criando um aplicativo](../ide/walkthrough-building-an-application.md)
